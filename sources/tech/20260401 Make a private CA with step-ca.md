[#]: subject: "Make a private CA with step-ca"
[#]: via: "https://fedoramagazine.org/make-a-private-ca-with-step-ca/"
[#]: author: "Stuart D Gathman https://fedoramagazine.org/author/sdgathman/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Make a private CA with step-ca
======

![][1]

[Image by freepik][2]

In this article you will learn how TLS (Transport Layer Security) and SSH (Secure SHell) use public/private key-pairs to authenticate web servers you visit and linux machines you log in to. You will also learn how the TLS framework installed by default in mainstream web browsers fails to prevent MITM (Man In The Middle) attacks in critical ways. Then we will walk through setting up a private .FEDORA TLD (Top Level Domain), setting up your own private CA with the smallstep package, and using the acme-tiny package to issue certificates for a website under that private TLD.

I will not cover setting up a simple “Hello World” website using your favorite web server packaged with Fedora. This needs to be up and running on HTTP to follow along. For this article, the website will be named hello.fedora.

Sadly, we will also explain how this does not completely solve the MITM problem – but this is already a big article. [Click here][3] to skip the background and motivation and go directly to the HowTo.

### How Public Keys Prevent Man-In-The-Middle Attacks

While NSA director Admiral Bobby revealed that intel agencies were aware of two key, or [public-key][4] cryptography since the 1960s, the first unclassified paper was published by [Whitfield Diffie][5] and [Martin E. Hellman][6] in 1976. In college, I remember playing with cryptosystems based on the [knapsack problem][7]. These had various vulnerabilities. What revolutionized the field was publication of the [RSA algorithm][8] in 1977. I vividly remember where I sat in the college library when I read the paper. There was some controversy over “you can’t patent algorithms”. However RSA patented their implementation (which is already protected by copyright – but that is another discussion). Yes, you can whip up a 1 line Perl implementation in a few minutes (we all did) – but a secure implementation that does not leak the private key through various [side channels][9] is NOT trivial.

The original concept of public keys was to look up a recipient’s pubkey in a directory, and use it to encrypt a message that only the possessor of the corresponding private key can decrypt. This can also be used to _authenticate_ a correspondent via a protocol that proves they hold the corresponding private key. The basic idea is to encrypt a random token with a pubkey, the recipient decrypts the token and sends it back encrypted by your pubkey. The details are not trivial. The primary concern is MITM attacks. SSH and TLS support several widely accepted algorithms for authentication and key exchange.

#### The Directory of Pubkeys is Critical

If you think about it, that “directory” is all important. Suppose you have a “secure” phone app (without naming names) that uses a public directory to map telephone number to pubkey. Whoever runs that directory can return their own pubkey (likely a different one for each telephone number), decrypt the data, and send it on, re-encrypted to the real pubkey of the intended recipient (and the same for the other direction). I.e. – the classic MITM attack. This is why such secure applications usually provide a way to verify you have the real pubkey via an in-person meeting or alternate medium.

So how do you know the real pubkey for a secure (https) website? Websites provide a “certificate” saying “this pubkey is for these domain names” (and other information we are not concerned with here). Well, anyone can create such a certificate – in fact we will do so in this article – so how do you know it is truthful? The certificate is “signed” by a Certificate Authority (CA). Pubkeys can be used to sign data. For RSA, the basic concept is to compute a secure “hash” (e.g. SHA256) of the certificate data, and “decrypt” it using the private key of the CA. The signature can be verified by using the pubkey of the CA to “encrypt” the result, – which should match the hash of the signed data. RSA is nice in that decryption and encryption are symmetrical – [verifying a signature][10] is the same operation as encrypting the signature to the owner of the privkey for the pubkey . So now, instead of every web user maintaining a private database of pubkeys for domain names, the browser has a list of trusted CAs which sign website certificates after verifying them in some way. In case a private key is compromised, CAs publish a Revocation List (which regular people rarely use) and TLS certificates always have an expiration date.

Note that CAs can certify data other than domain names, like the name of a company or individual. Commercial CAs generally charge a premium for this, but there are also non-profit CAs like [cacert.org][11] that certify personal details via in-person meetings.

### How Mainstream Browsers Know Which CAs to Trust

Regular Joes (“normies”) do not keep track of all this, so where does that “list of trusted CAs” come from? Well, there is a [CA and Browser forum][12] with representatives from popular browser software makers and commercial CAs. They maintain a list of trusted CAs, and changes are voted on in public meetings with minutes published on their web page. Fedora installs this list in /usr/share/pki. Browsers may have their own copy. Users may add additional trusted CAs to /usr/share/pki or /etc/pki/ca-trust and browsers may have their own way of adding additional trusted CAs.

This all sounds well and good, BUT. The critical flaw could be called [serial reliability][13]. The trusted CAs are trusted for any domain. So any trusted CA (including any you add) can forge a certificate for any website. DNS vulnerabilities (cache poisoning and such) are beyond the scope of this article. But we will set up a private CA which you could use to forge any website cert and fool anyone you convince to trust your CA (and can hack their DNS and/or IP routing). The cabforum is very careful about their list. As part of hostilities, forum CAs stopped certifying .RU domains (ISO TLD for Russia). Russia promptly put up their own national CAs, which anyone can add to their browser trust store. Normies were warned NOT to do this, as the Russian CAs could then forge certs for any domain. But a moment’s thought reveals that ANY cabforum CA could go “rogue” and do the same thing. It only takes one.

There are solutions to this blanket trust problem, but that will require another article.

### Create a private TLD with bind

For illustration, we will create the .FEDORA TLD. Everyone following along will create a different instance of that TLD, and hostnames under .FEDORA will resolve to different IPs (or NXDOMAIN) depending on whose DNS server you point that TLD at. This was the motivation for creating [ICANN][14] – a worldwide centralized DNS root (list of official TLDs). This provides a consistent namespace at the expense of absolute power (to cancel domains and TLDs) invested in ICANN. Before ICANN, admins all maintained their own DNS root, and periodically updated (manually or automatically) nameservers for well known TLDs like .COM etc. ISO defined an official list of TLDs, including country code TLDs (like .US). That worked well. The problem came with more obscure TLDs like .FREE. Companies trying to be “cool” were upset that not all customers got the same IPs for .FREE hostnames. Also admins liked having “someone else” maintain the DNS root. Hence, ICANN. There is also [Opennic][15] which likewise has “someone else” (volunteers) maintain a root zone, with fallback to ICANN, and has its own “forum” (existing TLDs vote) to approve new TLDs.

Here is a bind zonefile for .FEDORA:

```

    $TTL 2H
    ; hello.fedora
    @               IN      SOA     ns1     hostadmin.hello.fedora. (
                            2025122600 ; serial
                            1H ; refresh
                            15M ; retry
                            14D ; expire
                            6H ; default_ttl
                            )
    @               IN      NS      ns1.fedora.
    @               IN      TXT     "v=spf1 -all"
    hello         IN      A       192.168.100.31
    ns1         IN      A       192.168.100.31
    ca          IN      A       192.168.100.31

```

But that was a bait and switch. Setting up DNS for a private TLD is its own article. If you know how to add such a zone to your self hosted DNS – then do so. For the rest, we’ll use an even older hostname/IP map that predates DNS: as root, edit the file /etc/hosts on the system you will run step-ca on and append these lines:

```

    # smallstep article
    192.168.100.31      hello.fedora
    192.168.100.31        ca.fedora

```

Replace 192.168.100.31 with the IP of the system you are trying all this out on. Step-ca must be able to lookup the hello.fedora hostname it is certifying to do the ACME protocol. We will use the /.well-known/acme-challenge method, which does not require real DNS. The system you run acme-tiny on also needs to lookup ca.fedora.

### Run a private CA with step-ca

If the smallstep package is still under [review][16] when you read this, you’ll need to enable the [copr repo][17] (otherwise skip this step):

```

    sudo dnf copr enable @fedora-review/fedora-review-2418762-smallstep

```

#### Create root CA

First, we need to create our root CA. In production, this should be on a separate offline machine. For small operations, the secondary CAs can be automated, and you sign the certificates for these secondaries manually with the root CA. I would keep the root CA password on paper – can’t be hacked (but watch out for cameras). Do NOT skip the password for the root CA. Some number of systems will trust that CA for any domain. If the private key leaks, you end up with a situation like [Dell faced in 2015][18].

Let’s put the manual root CA in /etc/pki/CA and generate the root cert. Openssl will ask you for a key passwd, and what x509 calls “subject identifiers”. I left the state and email blank, and set city to Fedora City, organization to Fedora Project, organizational unit to ca, and common name to ca.example.org. The “-days 3650” sets the expiration to 10 years from now. The second command shows the “Issuer” information end-users will see when they ask for the issuer in an app like Firefox. The common name should normally be the hostname of the root CA, but it doesn’t really matter when the root CA is offline – and example.org is coincidentally offline by convention. 🙂

```

    $ sudo mkdir /etc/pki/CA
    $ cd /etc/pki/CA
    $ sudo install --mode=644 /dev/stdin root_ca.fedora.ext <<EOF
    subjectAltName=DNS:ca.example.org
    subjectKeyIdentifier = hash
    authorityKeyIdentifier = keyid:always,issuer
    basicConstraints = critical, CA:true, pathlen:1
    keyUsage = critical, digitalSignature, cRLSign, keyCertSign
    EOF
    $ sudo mkdir -m 0700 private
    $ sudo openssl req -new -keyout private/root_ca.key -out root_ca.csr
    ...
    $ sudo openssl x509 -req -in root_ca.csr -key private/root_ca.key -out root_ca.crt -days 3652 -sha256 -extfile root_ca.fedora.ext
    Enter pass phrase for private/root_ca.key:
    Certificate request self-signature ok
    subject=C=US, L=Fedora City, O=Fedora Project, OU=ca, CN=ca.example.org

```

#### Create intermediate certificate and install smallstep

Then install the smallstep package with [step-ca][19] binary and supporting files:

```

    $ sudo dnf install smallstep

```

The package installs a skeleton config for a step-ca service in /var/lib/step-ca. Let’s flesh out the config as step-ca and generate an intermediate cert request (“csr”).

```

    $ cd /var/lib/step-ca
    $ sudo -u step-ca bash -l
    $ ls
    certs  config  db  secrets  templates
    $ cp /etc/pki/CA/root_ca.crt certs
    $ openssl req -new -keyout secrets/intermediate_ca.key -out intermediate_ca.csr
    ...
    $ nano config/ca.json
    $ exit

```

Again, openssl will ask for subject identifiers. I used the same as for the root CA, but with the common name ca.fedora. Use your favorite text editor; “nano” is beginner friendly. Change MYCABAL to FEDORA and ca.mycabal.org to ca.fedora. If you provided a password for intermediate_ca.key, put it in the “password” field of ca.json. _Do not set the password in ca.json to the empty string._ This will make step-ca try to prompt for it at startup – which is not allowed under systemd, and fails with an error opening /dev/tty. For the intermediate cert, the common name is important. Smallstep will auto generate a host cert for “ca.fedora” (it is, after all, a certificate authority), and it must match the hostname ACME clients use to sign certs. Now we need to sign the intermediate cert with the root CA. 1825 days is 5 years. Intermediate certs should be shorter lived than the root CA. Not too short, if you are manually resigning the certs.

```

    $ cd /etc/pki/CA
    $ sudo install --mode=644 /dev/stdin ca.fedora.ext << EOF
    subjectAltName=DNS:ca.fedora
    subjectKeyIdentifier = hash
    authorityKeyIdentifier = keyid:always,issuer
    basicConstraints = critical, CA:true, pathlen:0
    keyUsage = critical, digitalSignature, cRLSign, keyCertSign
    EOF
    $ sudo openssl x509 -req -in /var/lib/step-ca/intermediate_ca.csr -CA root_ca.crt -CAkey private/root_ca.key -CAcreateserial -out intermediate_ca.crt -days 1825 -sha256 -extfile ca.fedora.ext
    $ sudo -u step-ca cp intermediate_ca.crt /var/lib/step-ca/certs
    $ sudo systemctl start step-ca
    $ sudo systemctl status step-ca
    ...
    Mar 31 15:18:56 test.gathman.org step-ca[2814912]: 2026/03/31 15:18:56 Serving HTTPS on :9000 ...

```

### Use httpd to serve hello.fedora web page

Running a web server was a prerequisite. I’ll use apache as an example, and hopefully users of nginx and others can translate. First, /etc/httpd/conf.d/hello.conf

```

    <VirtualHost *:80>
    ServerName      hello.fedora
    DocumentRoot    "/var/www/html/hello"
    #RedirectMatch ^((?!\/\.well-known\/).*)$ https://hello.fedora$1
    <Location "/.well-known/acme-challenge/">
            Options -Indexes
            Order allow,deny
            Allow from all
    </Location>
       <Location "/">
            Options FollowSymLinks Indexes
            Require all granted
        </Location>
    </VirtualHost>

```

The redirect is commented out until we have a signed cert. Assuming httpd is already running, use sudo apachectl graceful to load the changes. Then a simple document in /var/www/html/hello/index.html

```

    <html>
       <head>
                  <title> Hello Fedora </title>
     </head>
         <body>
                  <h1> Hello Fedora! </h1>
          </body>
    </html>

```

### Use acme-tiny to sign a TLS cert with step-ca

#### Add private root CA

Acme-tiny needs to trust the root CA to use the ACME service. The step-ca service provides a handy API to fetch the root ca:

```

    $ cd /etc/pki/ca-trust/source/anchors
    $ sudo curl https://ca.fedora:9000/roots.pem -o fedora_ca.crt
    curl: (60) SSL certificate problem: unable to get local issuer certificate

```

Ooops! Catch 22. You need the root CA to use the handy API that gets the root CA. So we’ll have to tell curl to accept the strange root cert. (Or use rsync, cp on the same machine, copy/paste between terminal windows, or other more secure method.)

```

    $ sudo curl -k https://ca.fedora:9000/roots.pem -o fedora_ca.crt
    $ sudo update-ca-trust extract

```

Now, we are ready to run acme-tiny. Once again, openssl req will prompt for subject identifiers. The only one browsers care about is Common Name, which should be “hello.fedora”. However, users may care about the other fields when they use browser features to inspect certs.

```

    $ sudo dnf install acme-tiny
    $ sudo apachectl graceful
    $ cd /var/lib/acme
    $ sudo -u acme bash -l
    $ ls
    certs  csr  private
    $ /usr/libexec/acme-tiny/sign  # NOTE: generates account.key if needed
    $ ls private
    account.key
    $ openssl req -new -passout pass:'' -keyout private/hello.key -out csr/hello.csr
    $ /usr/sbin/acme_tiny --account-key private/account.key --csr csr/hello.csr --acme-dir /var/www/challenges/ --ca https://ca.fedora:9000/acme/FEDORA >certs/hello.crt
    $ exit
    $ sudo nano /etc/httpd/conf.d/hello.conf

```

Now uncomment the Redirect Match and append the below SSL virtual host definition to hello.conf. Use apachectl graceful to load the changes.

```

    <VirtualHost *:443>
    ServerName      hello.fedora:443
    SSLEngine on
    SSLProtocol all -SSLv2 -SSLv3
    SSLCipherSuite HIGH:3DES:!aNULL:!MD5:!SEED:!IDEA
    DocumentRoot    "/var/www/html/hello"
    SSLCertificateFile /var/lib/acme/certs/hello.crt
    SSLCACertificateFile /var/lib/acme/certs/hello.crt
    SSLCertificateKeyFile /var/lib/acme/private/hello.key
    CustomLog logs/ssl_request_log \
              "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
       <Location "/">
            Options FollowSymLinks Indexes
        </Location>
    </VirtualHost>

```

The current acme-tiny package auto-renews certs only for the letsencrypt.org CA. That should be extended soon. Meanwhile, feel free to add something hacky. (I’ll try to have it lookup tlds in /etc/sysconfig or something to get custom CA url.)

### Use a browser to display the web page

On the machine with your web browser, you need 2 things: the new root CA and some way to lookup names in the .FEDORA TLD, either by pointing DNS to the server you set up with the private zone, or by appending the lines to /etc/hosts for ca.fedora and hello.fedora.

Now the curl should work without -k. And your browser should work to display <https://hello.fedora>, although you might have to restart it. If it doesn’t read Fedora ca-trust store on startup, you might need to find an option to import CA on the browser menu.

```

    $ curl https://hello.fedora
    <html>
      <head>
                  <title> Hello Fedora </title>
     </head>
         <body>
                  <h1> Hello Fedora! </h1>
          </body>
    </html>

```

Now, that your root CA is up and running, don’t lose sight of what can be done by having it go rogue. Get lots of people to install it so they can access your cool new TLDS. Then start forging certs for arbitrary web sites, and conquer the world!! Bwa! ha! ha! (A future article can address PKCS#11 and restricting how you trust CAs in browsers and other software.)

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/make-a-private-ca-with-step-ca/

作者：[Stuart D Gathman][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/sdgathman/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/02/CA_image-816x345.jpg
[2]: https://www.freepik.com/free-photo/education-diploma-certificate-template_11330056.htm
[3]: tmp.Ama1ljFzIL#stepbystep
[4]: https://www.britannica.com/topic/public-key-cryptography
[5]: https://www.britannica.com/biography/Whitfield-Diffie
[6]: https://www.britannica.com/biography/Martin-E-Hellman
[7]: https://en.wikipedia.org/wiki/Knapsack_problem
[8]: https://www.geeksforgeeks.org/computer-networks/rsa-algorithm-cryptography/
[9]: https://www.techtarget.com/searchsecurity/definition/side-channel-attack
[10]: https://en.wikipedia.org/wiki/RSA_cryptosystem#Verifying
[11]: http://cacert.org
[12]: https://cabforum.org/
[13]: https://www.globalspec.com/reference/75483/203279/chapter-1-reliability-of-series-systems
[14]: https://www.icann.org/
[15]: https://opennic.org
[16]: https://bugzilla.redhat.com/show_bug.cgi?id=2418762
[17]: https://copr.fedorainfracloud.org/coprs/build/9864495
[18]: https://krebsonsecurity.com/2015/11/security-bug-in-dell-pcs-shipped-since-815/
[19]: https://github.com/smallstep/certificates
