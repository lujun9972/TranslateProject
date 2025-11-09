[#]: subject: "7 Privacy Wins You Can Get This Weekend (Linux-First)"
[#]: via: "https://itsfoss.com/privacy-wins-linux/"
[#]: author: "Theena Kumaragurunathan https://itsfoss.com/author/theena/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

7 Privacy Wins You Can Get This Weekend (Linux-First)
======

[![Warp Terminal][1]][2]

Privacy is a practice. I treat it like tidying my room. A little attention every weekend keeps the mess from becoming a monster. Here are seven wins you can stack in a day or two, all with free and open source tools.

### 1\. Harden your browser

Firefox is still the easiest place to start. Install **uBlock Origin** , turn on strict tracking protection, and only whitelist what you truly need. Add NoScript if you want to control which sites can run scripts.

  * Why it matters: Most tracking starts in the browser. Blocking it reduces profiling and drive‑by nasties.
  * How to do it: In Firefox settings, set Enhanced Tracking Protection to Strict. Install uBlock Origin. If you’re comfortable, install NoScript and allow scripts only on trusted sites.
  * Trade‑off: Some pages break until you tweak permissions. You’ll learn quickly which sites respect you.



### 2\. Search without surveillance

Shift your default search to privacy‑respecting frontends and engines. SearXNG is a self‑hostable metasearch. Startpage, if you want something similar to Google, although excessive ads on their search page is a turn-off.

  * Why it matters: Your searches reveal intent and identity. Reducing data capture lowers your footprint.
  * How to do it: Set your browser’s default search to DuckDuckGo or Startpage or a trusted SearXNG instance. Consider hosting SearXNG later if you enjoy tinkering.
  * Trade‑off: Results can feel slightly different from Google. For most queries, they’re more than enough.



📋

The article contains some partnered affiliate links. Please read our [affiliate policy][3].

### 3\. Block ads and trackers on your network

![][4]

A [Pi‑hole][5] or [AdGuard Home][6] (partner link) box filters ads for every device behind your router. It’s set‑and‑forget once configured. **AdGuard is not open source** but a trusted mainstream service.

  * Why it matters: Network‑level filtering catches junk your browser misses and protects smart TVs and phones.
  * How to do it: Install Pi‑hole or AdGuard Home on a Raspberry Pi or a spare machine. Point your router’s DNS to the box.
  * Trade‑off: Some services rely on ad domains and may break. You can whitelist specific domains when needed.



![Photo by Matthew Henry / Unsplash][7]

### 4\. Private DNS and a lightweight VPN

Encrypt DNS with [DNS‑over‑HTTPS][8] and use WireGuard for a fast, modern VPN. Even if you only use it on public Wi‑Fi, it’s worth it.

  * Why it matters: DNS queries can expose your browsing. A VPN adds another layer of transport privacy.
  * How to do it: In Firefox, turn on DNS‑over‑HTTPS. Set up WireGuard with a reputable provider or self‑host if you have a server.
  * Trade‑off: A tiny speed hit. Misconfiguration can block certain services. Keep a fallback profile handy.



### 5\. Secure messaging that respects you

[Signal][9] is my default for personal chats. It’s simple, secure, and widely adopted. The desktop app keeps conversations synced without drama.

  * Why it matters: End‑to‑end encryption protects content even if servers are compromised.
  * How to do it: Install Signal on your phone, then link the desktop app. Encourage your inner circle to join.
  * Trade‑off: Not everyone will switch. That’s fine. Use it where you can.



### 6) Passwords and 2FA, properly

Store strong, unique passwords in KeePassXC and use time‑based one‑time codes. You’ll never reuse a weak password again. Use [ProtonPass][10] if you want a more mainstream option.

  * Why it matters: Credential stuffing is rampant. Unique passwords and 2FA stop it cold.
  * How to do it: Create a [KeePassXC][11] vault, generate 20‑plus character passwords, and enable TOTP for accounts that support it. Back up the vault securely.
  * Trade‑off: A small setup hurdle. After a week, it becomes second nature.



![][12]

### 7) Email with privacy in mind

Use [ProtonMail][13] for personal email. Add aliasing to keep your main address clean. For newsletters, pipe them into an RSS reader so your inbox isn’t a tracking playground.

  * Why it matters: Email carries identity. Aliases cut spam, and RSS limits pixel tracking.
  * How to do it: Create a Proton account. Use aliases for sign‑ups. Subscribe to newsletters via RSS feeds if available or use a privacy‑friendly digest service.
  * Trade‑off: Some newsletters force email only. Accept a separate alias or unsubscribe.



### Good, Better, Best

  * **Browser**
Good: Firefox with uBlock Origin.
Better: Add NoScript and tweak site permissions.
Best: Harden about:config and use containers for logins.
  * **Search**
Good: Startpage as default.
Better: Use a trusted SearXNG instance.
Best: Self‑host SearXNG and monitor queries.
  * **Network filtering**
Good: Pi‑hole or AdGuard Home on a spare device.
Better: Add curated blocklists and per‑client rules.
Best: Run on a reliable server with automatic updates and logging.
  * **DNS and VPN**
Good: Browser DNS‑over‑HTTPS.
Better: System‑wide DoH or DoT.
Best: WireGuard with your own server or a vetted provider.
  * **Messaging**
Good: Signal for core contacts.
Better: Encourage groups to adopt.
Best: Use disappearing messages and safety numbers.
  * **Passwords and 2FA**
Good: KeePassXC vault and TOTP for key accounts.
Better: Unique passwords everywhere and hardware‑encrypted backups.
Best: Hardware tokens where supported plus KeePassXC.
  * **Email**
Good: Proton for personal mail.
Better: Aliases per service.
Best: RSS for newsletters and strict filtering rules.



### Time to implement

  * Quick wins: Browser hardening, search swap, Signal setup. About 60 to 90 minutes.
  * Medium: KeePassXC vault, initial 2FA rollout. About 90 minutes.
  * Weekend projects: Pi‑hole or AdGuard Home, WireGuard. About 3 to 5 hours depending on your comfort.



### Conclusion

Start with what you control. The browser, your passwords, your default search. Privacy is cumulative. One small change today makes the next change easier tomorrow. If you keep going, the internet feels calmer, like you finally opened a window in a stuffy room.

--------------------------------------------------------------------------------

via: https://itsfoss.com/privacy-wins-linux/

作者：[Theena Kumaragurunathan][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/theena/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/affiliate-policy/
[4]: https://itsfoss.com/content/images/2025/11/image-4.png
[5]: https://itsfoss.com/setup-pi-hole/
[6]: https://adguard.com/?aid=135612
[7]: https://images.unsplash.com/photo-1461685265823-f8d5d0b08b9b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3wxMTc3M3wwfDF8c2VhcmNofDF8fHByaXZhY3l8ZW58MHx8fHwxNzYxNDczMjM5fDA&ixlib=rb-4.1.0&q=80&w=2000
[8]: https://developers.cloudflare.com/1.1.1.1/encryption/dns-over-https/
[9]: https://signal.org/
[10]: https://go.getproton.me/aff_c?offer_id=38&aff_id=1173
[11]: https://itsfoss.com/keepassxc/
[12]: https://itsfoss.com/content/images/icon/android-chrome-512x512.png
[13]: https://go.getproton.me/aff_c?offer_id=37&aff_id=1173
