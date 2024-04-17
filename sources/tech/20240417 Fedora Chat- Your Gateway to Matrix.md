[#]: subject: "Fedora Chat: Your Gateway to Matrix"
[#]: via: "https://fedoramagazine.org/fedora-chat-your-gateway-to-matrix/"
[#]: author: "Robert WrightDavid Cantrell https://fedoramagazine.org/author/rwright/https://fedoramagazine.org/author/dcantrell/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora Chat: Your Gateway to Matrix
======

![][1]

Photo by [Tom Gainor][2] on [Unsplash][3]

## **What is Matrix?**

[Matrix][4] is an open protocol for decentralized, secure communications built on the principles of interoperability and decentralization. You can create an account on a home server and then join channels across different home servers. This means if you have an account through Matrix.org, you can use it to join our community spaces! One of those is Fedora Chat.

[The Matrix Foundation][5] acts as the guardian of the Matrix protocol, ensuring it remains a free and open standard for secure, decentralized communication. It’s responsible for developing and maintaining the [Matrix Specification][6] along with working closely with the community to enhance interoperability and innovation.

## **What is Fedora Chat?**

Fedora Chat is what we call our Matrix homeserver instance. It is a set of two homeservers, one for our community rooms as fedoraproject.org as well as the fedora.im homeserver which provides accounts for our users to join the fedoraproject.org rooms. Both of these are hosted by Element Matrix Services (“EMS”) thanks to our sponsorship from Red Hat.

You can use your fedora.im account to join other Matrix homeservers as well and collaborate with other communities, including [Gnome][7], [Mozilla][8], and [Ubuntu][9]!

### **Getting Started on Fedora Chat**

Ready to jump into Fedora Chat? If you do not have a Matrix account already, you can use the fedora.im homeserver to get an account and join our community space! If you already have Matrix – [you can join our Fedora space through this link][10].

  1. Visit[ https://chat.fedoraproject.org][11] and click the blue “Sign in” and then “Continue with your Fedora Account” to login with your FAS account.
  2. You should be added to our Space automatically which is a collection of rooms, but if not, join the room here [#fedora-space:fedoraproject.org][10]
  3. You can then choose different rooms in the menu in which to say hello. Find a room and then say hello!



## **Exploring Other Matrix Clients**

While Fedora Chat uses the hosted Element client, the Matrix universe is vast. Explore other clients that suit your needs, from desktop apps to mobile solutions. Each offers unique features, allowing you to tailor your experience. You can find an updated list of [different clients on the Matrix.org website][12].

## **Understanding Encryption, Keys, and Device Verification**

Matrix’s end-to-end encryption ensures that only the communicating users in a room can read messages. Some rooms are end-to-end encrypted, but most public rooms are not. Most rooms in Fedora community spaces are not end-to-end encrypted, and you can see the history. However, if you directly message another user or join an E2E room, your messages will be encrypted by default. This is achieved through the management of cryptographic keys that secure each conversation. The encryption process involves generating unique keys your client stores on your behalf.

Protecting your encryption keys is essential, and your Recovery Key is critical to keep. The Recovery Key allows you to restore access to your encrypted conversations if you lose access to your primary key backup. Keep your Recovery Key in a safe location.

Session verification further enhances security by allowing users to verify their identity across multiple devices, ensuring that verified devices can only read encrypted messages.

[Element provides a great FAQ on how to create and manage your key backups][13], but this will vary based on the client you choose to use. If you use chat.fedoraproject.org, it is a great resource.

## **What’s Next**

Join [#fedora-space:fedoraproject.org][10] and say hello in [#intros:fedoraproject.org][14] – and welcome to the Matrix-verse!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/fedora-chat-your-gateway-to-matrix/

作者：[Robert WrightDavid Cantrell][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/rwright/https://fedoramagazine.org/author/dcantrell/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/04/gateway-816x346.jpg
[2]: https://unsplash.com/@its_tgain?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/arch-landmark-N9PCtj8wdFg?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://matrix.org/
[5]: https://matrix.org/about/
[6]: https://spec.matrix.org/latest/
[7]: https://wiki.gnome.org/GettingInTouch/Matrix
[8]: https://wiki.mozilla.org/Matrix
[9]: https://ubuntu.com/community/communications/matrix
[10]: https://matrix.to/#/#fedora-space:fedoraproject.org
[11]: https://chat.fedoraproject.org
[12]: https://matrix.org/ecosystem/clients/
[13]: https://element.io/help#encryption
[14]: https://matrix.to/#/#intros:fedoraproject.org
