[#]: subject: "SSH into Raspberry Pi from Outside Home Network Using Tailscale"
[#]: via: "https://itsfoss.com/tailscale-raspberry-pi-ssh/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

SSH into Raspberry Pi from Outside Home Network Using Tailscale
======

[![Warp Terminal][1]][2]

Earlier, I shared [how you can use Cloudflare Tunnels to access Raspberry Pi outside your home network][3].

A few readers suggested using Tailscale. And indeed, this is a handy tool if your aim is to [ssh into your Raspberry Pi][4] securely from outside your home network.

In this article, I'll be covering how you can use **Tailscale VPN** to remotely connect to your Raspberry Pi without the hassle of complicated network setups.

### What is Tailscale?

[Tailscale][5] is a zero-config VPN built on the [WireGuard protocol][6], designed to securely connect devices across different networks as if they were on the same local network.

It simplifies private networking by establishing a mesh VPN that routes traffic between your devices, no matter where they are.

![][7]

Tailscale is available for multiple platforms, including Linux, macOS, Windows, Android, and embedded devices like the Raspberry Pi, making it a versatile solution for remote access.

![][8]

### How Tailscale Works

At the heart of Tailscale is [WireGuard][6], a fast and modern VPN protocol.

Tailscale uses this protocol to create encrypted connections between your devices, while managing all the networking complexities behind the scenes.

Its key mechanics include:

  * **Mesh Networking** : Devices in your Tailscale network (or "tailnet") connect directly to each other where possible, creating a mesh of encrypted connections.
  * **End-to-End Encryption** : All traffic is encrypted from one device to another, ensuring privacy and security.
  * **NAT Traversal** : Tailscale automatically handles NAT traversal and firewall configurations, so you don’t need to worry about setting up port forwarding or exposing services.
  * **Auto-Routing** : Once your devices are connected to the tailnet, Tailscale automatically routes traffic between them as needed.



This makes it an excellent option for remotely accessing your Raspberry Pi or any other device, eliminating the hassle of configuring VPNs, firewalls, or DNS settings.

### Installing Tailscale on Raspberry Pi

Tailscale can be installed easily on any Linux-based system, including the Raspberry Pi. Here’s how to set it up:

Update your system:

```

    sudo apt update && sudo apt upgrade -y

```

Install Tailscale:

```

    curl -fsSL https://tailscale.com/install.sh | sh

```

![][9]

Authenticate and connect to Tailscale:

```

    sudo tailscale up

```

![][10]

This command will generate a URL. Open this URL in your browser to log in with your Tailscale account. Once authenticated, your Raspberry Pi will be connected to your tailnet.

Access Your Raspberry Pi: Once your Pi is part of the tailnet, you can access it remotely using its Tailscale IP address.

```

    ssh pi@<tailscale-ip>

```

![][11]

#### Setting Up Your Tailscale Network (Tailnet)

Once you’ve created your [Tailscale account][12], you’ll need to set up your tailnet and connect devices to it.

**Tailnet Creation** : The good news is that Tailscale automatically creates a tailnet for you when you log in.

There's no need for manual network setup just install Tailscale on your devices and they’ll join the same tailnet.

![][13]

**Tailnet IP Addresses** : Every device that joins your tailnet gets its own private, secure IP address.

These IP addresses are assigned automatically by Tailscale and can be used to remotely access your devices.

![][14]

**Managing Devices** : Once a device joins your tailnet, you can view and manage it from the Tailscale web dashboard.

From here, you can see the connection status, IP address, and name of each device. You can also remove devices or disable connections if needed.

![][15]

With your tailnet set up, you’re ready to access your Raspberry Pi from anywhere in the world, securely and without any complicated network configurations.

### Pricing

Tailscale offers a straightforward pricing structure, starting with a **Free Tier** that supports up to **100 devices** and includes all the key features needed for secure remote access—no credit card required.

For users needing more, the **Personal Pro** plan is **$5 per user per month** , with unlimited devices and 1 subnet router, while the **Business Plan** at **$10 per user per month** adds advanced features like ACLs and more subnet routers.

The **Enterprise Plan** offers custom solutions for larger networks.

For most personal projects, the Free Tier provides everything you need to get started easily.

![][16]

### Conclusion

Tailscale offers a simple solution for those needing simple, secure remote access to their Raspberry Pi or any other device.

By leveraging WireGuard for fast and encrypted connections, and simplifying the complexities of VPN setup, Tailscale allows you to focus more on your projects and less on network configuration.

The ease of installation, makes it an excellent choice for beginners, developers, and home automation enthusiasts alike.

If you have any suggestions for other apps or services you’d like us to cover, or if you want to share what systems you use for remote access, feel free to comment below! We'd love to hear your thoughts and experiences.

--------------------------------------------------------------------------------

via: https://itsfoss.com/tailscale-raspberry-pi-ssh/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/cloudflare-tunnels/
[4]: https://itsfoss.com/ssh-into-raspberry/
[5]: https://tailscale.com/
[6]: https://www.wireguard.com/
[7]: https://itsfoss.com/content/images/2024/10/tailscale-homepage.png
[8]: https://itsfoss.com/content/images/2024/10/tailscale-downloads-page.png
[9]: https://itsfoss.com/content/images/2024/10/tailscale-install-script.png
[10]: https://itsfoss.com/content/images/2024/10/tailscale-connect-link.png
[11]: https://itsfoss.com/content/images/2024/10/tailscale-ssh-setup.png
[12]: https://login.tailscale.com/start
[13]: https://itsfoss.com/content/images/2024/10/tailscale-connect-device-3.png
[14]: https://itsfoss.com/content/images/2024/10/tailscale-ip-addr-2.png
[15]: https://itsfoss.com/content/images/2024/10/tailscale-dashboard-1.png
[16]: https://itsfoss.com/content/images/2024/10/tailscale-pricing-1.png
