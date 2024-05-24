[#]: subject: "How to move from Redis to Valkey"
[#]: via: "https://fedoramagazine.org/how-to-move-from-redis-to-valkey/"
[#]: author: "Kyle Davis https://fedoramagazine.org/author/linuxmclinuxface/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to move from Redis to Valkey
======

![][1]

Photo by [Maxim Tolchinskiy][2] on [Unsplash][3]

The Redis move to a new license means it will no longer be considered open source software. This article will explain how to move from Redis to the alternative, Valkey.

### Background

A few weeks ago, the company behind Redis published a blog post announcing that future versions of the Redis project were moving from BSD-3 clause, a well-accepted and understood open source license, to dual RSALv2 (Redis Source Available License 2.0) / SSPLv1 (Server Side Public License). The [blog post plainly states][4] _“we openly acknowledge that this change means Redis is no longer open source under the OSI definition”_ (and, indeed, [Fedora doesn’t allow either of these licenses][5]).

In response to this change, a number of existing contributors and maintainers of Redis formed [Valkey, a new Linux Foundation project][6]. You can think of Valkey as a continuation of open source Redis. It is derived from the same code-base and has many of the same folks making the decisions and contributing. The Valkey project has a technical steering committee that consists of people that work at Alibaba, AWS, Ericsson, Huawei, Google, and Tencent and an even wider array of organizations as contributors.

### How do you move?

As a Fedora user, what are you to do if you use Redis and want to move to Valkey? Thankfully, there is the [_valkey-compat-redis_ package][7] to handle the transition for you by moving your data and configuration over to Valkey.

In this scenario, you likely already have Redis installed, running, and loaded with data. For the purpose of this post I started with a fresh Fedora 40 installation, added the Redis (7.2.4) package, and started the server.

From here I’m going to take a peek at the current redis server information:

```

    $ redis-cli info server
    # Server
    redis_version:7.2.4
    redis_git_sha1:00000000
    redis_git_dirty:0
    redis_build_id:8c22b097984bd350
    redis_mode:standalone
    ...

```

Note that the server responds with *redis_version:7.2.4 , *remember this for later.

Since this is a fresh install of Redis, I’m going to write some data to a key so it will be visible later in Valkey.

```

    $ redis-cli set test_key "written in redis 7.2.4"

```

### Migration and Persistence

Now is a good time to consider your persistence settings. How you persist your data in Redis (and Valkey) is highly configurable. Valid usage patterns run the gamut from no persistence whatsoever all the way to disk writes on every key change. _valkey-compat-redis_ will cleanly shut down Redis using _SIGTERM, _but there isn’t any additional magic: if you don’t have persistence set up or you have the Redis configuration (_ /etc/redis/redis.conf_) option *shutdown-on-sigterm *set to _now_ or _force_ you could lose some or all your data. However, keep in mind that running *valkey-compat-redis *isn’t functionally different from doing any previous Redis upgrade in this regard

### Installing the compat package

With that out of the way, it’s time to move to Valkey!

Install *valkey-compat-redis *with the _allowerasing_ flag. You need the *allowerasing _flag_ *so the package manager can remove Redis and put Valkey in its place.

```

    $ sudo dnf install valkey-compat-redis --allowerasing

    ...

    Installed:
      valkey-7.2.5-5.fc40.x86_64                               valkey-compat-redis-7.2.5-5.fc40.x86_64
    Removed:
      redis-7.2.4-3.fc40.x86_64

    Complete!

```

What did this just do? The package takes your [existing configuration files and persistence data and moves them to Valkey][8]. Valkey is able to accept these directly with no changes or translation steps. Valkey is fully compatible with the Redis API, protocol, persistence data, ports, and configuration files.

This is all possible because the current generally available release of Valkey (7.2.5) is, in practical purposes, a name change from Redis 7.2.4. The code changes in Valkey 7.2.5 were about re-branding. This version intentionally introduced no new features or functionality to make sure you can move to Valkey easily.

### Starting Valkey

Now that you’ve installed Valkey, you’ll need to start it:

```

    $ sudo systemctl start valkey

```

Then get the info about the server:

```

    $ redis-cli info server
    # Server
    redis_version:7.2.4
    server_name:valkey
    valkey_version:7.2.5
    redis_git_sha1:00000000
    redis_git_dirty:0
    redis_build_id:b0d9f188ef999bd3
    redis_mode:standalone
    ...

```

A few things to note in this example:

  * Valkey responds with *redis_version:7.2.4 *as well as *valkey_version:7.2.5 . *Some software has specific checks for versions and could break on an unknown response. Retaining *redis_version * maintains maximum compatibility while still identifying the server with _valkey_version._
  * Valkey has a binary named *valkey-cli *but symbolically links _redis-cli_. This will keep your muscle memory intact until you get used to typing _valkey-cli_. It does the same for _valkey-server_ and _redis-server_



### Interacting with Valkey

Now, it’s time to take a look at the data and interact with the server. First get the key that was written in Redis (of course, if you don’t have persistence turned on this won’t work):

```

    $ valkey-cli get test_key
    "written in redis 7.2.4"

```

Just as a proof point, you can write data to the server and get the key back written in Valkey along side the one written in Redis:

```

    $ valkey-cli set from-new-server "valkey-7.2.5"
    OK
    $ valkey-cli mget test_key from-new-server
    1) "written in redis 7.2.4"
    2) "valkey-7.2.5"

```

This example is pretty simple, but it illustrates a lot. First, because _valkey-compat-redis_ moves your configuration over, it doesn’t need to be the default. No matter how you have configured Redis 7.2.4, *valkey-compat-redis *moves simple or complex configurations over and Valkey can read them. This means that the same migrations step works even for Cluster or Sentinel.

Second, since Valkey connects in the same way (using the same protocols and default port) your application should work the same. Passing in the same connection information to your application that once pointed at Redis (and now points to Valkey) will yield the same results.

### Other Considerations

All of this being said: there are a few things that can’t be illustrated in the above example. You don’t _have_ to use _valkey-compat-redis_ , instead you can just install _[valkey][9]_. If you’ve got Redis on a machine and run:

```

    $ sudo dnf install valkey

```

You’ll have Valkey installed along side of Redis. You can’t successfully start up both processes using the default configuration. However, changing the configuration file at* /etc/valkey/valkey.conf *to use a different port would allow you to run Valkey and Redis. Indeed, you could even cluster Valkey and Redis together since they speak the same protocol, enabling more complex migrations.

The other thing to keep in mind is that Valkey isn’t any more backwards compatible than Redis 7.2.4. Moving from a very old version of Redis to Valkey carries the same breaking changes as moving to Redis 7.2.x. Thankfully, most versions carry minimal breaking changes even between major versions.

### What’s next?

This post has largely focused on what *hasn’t *changed and why that’s a good thing. The Valkey team intends to add no new features to 7.2.x. Only bug fixes coming as patch releases will occur in the future. All new changes are going in 8.x. While the team is busy planning a full slate of new features that increase performance and usability, they don’t plan to break the API. If you’re interested in helping work on the future of Valkey, be sure to check out[ valkey-io/valkey ][10]and read the [CONTRIBUTING.md][11] file to learn more.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/how-to-move-from-redis-to-valkey/

作者：[Kyle Davis][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/linuxmclinuxface/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/05/move_from_redis_to_valkey-816x345.jpg
[2]: https://unsplash.com/@shaikhulud?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/white-truck-parked-near-white-building-crHhZlES310?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://redis.io/blog/redis-adopts-dual-source-available-licensing/
[5]: https://docs.fedoraproject.org/en-US/legal/allowed-licenses/
[6]: https://www.linuxfoundation.org/press/linux-foundation-launches-open-source-valkey-community
[7]: https://packages.fedoraproject.org/pkgs/valkey/valkey-compat-redis/
[8]: https://src.fedoraproject.org/rpms/valkey/blob/rawhide/f/migrate_redis_to_valkey.sh
[9]: https://packages.fedoraproject.org/pkgs/valkey/valkey/
[10]: https://github.com/valkey-io/valkey
[11]: https://github.com/valkey-io/valkey/blob/unstable/CONTRIBUTING.md
