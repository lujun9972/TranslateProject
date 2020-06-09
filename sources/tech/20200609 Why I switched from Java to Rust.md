[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Why I switched from Java to Rust)
[#]: via: (https://opensource.com/article/20/6/why-rust)
[#]: author: (Mike Bursell https://opensource.com/users/mikecamel)

Why I switched from Java to Rust
======
Rust feels like the place to be: it's well-structured, it's expressive,
it helps you do the right thing.
![Person programming on a laptop on a building][1]

I recently started [learning Rust][2] after many years of Java development. The five points that keep coming to mind are:

  1. Rust feels familiar
  2. References make sense
  3. Ownership _will_ make sense
  4. Cargo is helpful
  5. The compiler is amazing



I absolutely stand by all of these, but I've got a little more to say because I now feel like a Rustacean[1][3] in that:

  * I don't feel like programming in anything else ever again.
  * I've moved away from simple incantations.



What do I mean by these two statements? Well, the first is pretty simple: Rust feels like the place to be. It's well-structured, it's expressive, it helps you do the right thing,[2][4] it's got great documentation and tools, and there's a fantastic community. And, of course, it's all open source, which is something that I care about deeply.

Here is an example of what it is like to use Rust:


```
// Where checkhashes is pre-defined vector of hashes to verify
let algorithms = vec![String::from("SHA-256"); checkhashes.len()];
```

This creates a new vector called "algorithms," of the same length as the vector "checkhashes," and fills it with the String "SHA-256." And the second thing? Well, I decided that in order to learn Rust properly, I should take a project that I had originally written in Java and reimplement it in hopefully fairly idiomatic Rust. Before long, I started fixing mistakes—and making mistakes—around implementation rather than around syntax. And I wasn't just copying text from tutorials or making minor, seemingly random changes to my code based on the compiler output. In other words, I was getting things to compile, understanding why they compiled, and then just making programming mistakes.[3][5]

Here's another example, which should feel quite familiar:


```
fn usage() {
    println!("Usage: findfromserial KEY_LENGTH INITIAL_SALT CHECK_HASH1 [CHECK_HASH2, ...]");
    std::process::exit(1);
}
```

This is a big step forward. When you start learning a language, it's easy just to copy and paste text that you've seen elsewhere, or fiddle with unfamiliar constructs until they—sort of—work. Using code or producing code that you don't really understand but seems to work is sometimes referred to as "using incantations" (from the idea that most magicians in fiction, film, and gaming recite collections of magic words that "just work" without really understanding what they're doing or what the combination of words actually means). Some languages[4][6] are particularly prone to this sort of approach, but many—most?—people learning a new language are prone to doing this when they start out just because they want things to work.

Recently, I was up until 1am implementing a new feature—accepting command-line input—that I couldn't really get my head 'round. I'd spent quite a lot of time on it (including looking for—and failing to find—some appropriate incantations), and then asked for some help on an internal rust-lang channel. (You might want to sign up to the [general Slack Rust channel][7] inhabited by some people I know.) A number of people had made some suggestions about what had been going wrong, and one person was enormously helpful in picking apart some of the suggestions, so I understood them better. He explained quite a lot, but finished with, "I don't know the return type of the hash function you're calling—I think this is a good spot for you to figure this piece out on your own."

Here's where I was trying to get to:


```
checkhashes = std::env::args()
    .skip(3)
    .map(|x| hex::decode(x))
    .collect::&lt;Result&lt;Vec&lt;Vec&lt;u8&gt;&gt;, _&gt;&gt;()
    .unwrap();
```

It may seem weird until you get your head 'round it, but it actually works as you might expect: I wanted to take input from the command line, skip the first three inputs, iterate over the rest, casting each to a vector of u8's and creating a vector of those. The `_` at the end of the "collect" call vacuums up any errors or problems and basically throws them away.

This was just what I needed, and what any learner of anything, including programming languages, needs. So when I had to go downstairs at midnight to let the dog out, I decided to stay down and see if I could work things out for myself. And I did. I took the suggestions that people had made, understood what they were doing, tried to divine what they _should_ be doing, worked out how they should be doing it, and then found the right way of making it happen.

I've still got lots to learn, and I'll make lots of mistakes still, but I now feel that I'm in a place to find my way through those mistakes (with a little help along the way, probably—thanks to everyone who's already pointed me in the right direction). But I do feel that I'm now actually programming in Rust. And I like it.

* * *

  1. This is what Rust programmers call themselves.
  2. It's almost impossible to stop people doing the wrong thing entirely, but encouraging people to do the right thing is great. In fact, Rust goes further and actually makes it _difficult_ to do the wrong thing in many situations. You really have to try quite hard to do bad things in Rust.
  3. I found a particularly egregious off-by-one error in my code, for instance, which had nothing to do with Rust, and everything to do with my not paying enough attention to the program flow.
  4. _Cough_ Perl _cough_



* * *

_This article is based on [More Rusty thoughts][8] on Alice, Eve and Bob – a security blog and is reused with permission._

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/why-rust

作者：[Mike Bursell][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/mikecamel
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/computer_code_programming_laptop.jpg?itok=ormv35tV (Person programming on a laptop on a building)
[2]: https://opensource.com/article/20/5/rust-java
[3]: tmp.Sjxya3HUQg#1
[4]: tmp.Sjxya3HUQg#2
[5]: tmp.Sjxya3HUQg#3
[6]: tmp.Sjxya3HUQg#4
[7]: https://rust-slack.herokuapp.com/
[8]: https://aliceevebob.com/2020/05/19/more-rusty-thoughts/
