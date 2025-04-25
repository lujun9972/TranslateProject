[#]: subject: "Enabling system-wide DNS over TLS"
[#]: via: "https://fedoramagazine.org/enabling-system-wide-dns-over-tls/"
[#]: author: "Pavel BřezinaFrancisco Trivino Garcia https://fedoramagazine.org/author/pbrezina/https://fedoramagazine.org/author/ftrivino/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Enabling system-wide DNS over TLS
======

![][1]

Enigma Machine Photo by [Christian Lendl][2] on [Unsplash][3] Cropped

This article will guide you to enforcing DoT (DNS over TLS) on your running system and at boot time. Support is avaliable in Fedora 42. It will also guide you to set up encrypted DNS for system installation, if you want to try it with current Fedora Rawhide (Fedora 43).

### Background

Traditionally, DNS queries are transferred over unencrypted datagrams through UDP port 53. This unencrypted nature provides a potential attack vector when an attacker is able to easily capture and modify DNS requests and responses. This can be mitigated by using encrypted DNS protocols such as DNS over TLS (DoT) and DNS over HTTPS (DoH).

Fedora has built in support for DNS over TLS through systemd-resolved, which is the default DNS resolver since Fedora 33. It is also possible to configure enforced or opportunistic DoT via DNSoverTLS option in resolved.conf. However, this only enables DNS encryption for system runtime. This is not enough on Zero Trust Networks where all DNS communication has to be encrypted for system runtime as well as during boot time for network boots and during system installation.

A Red Hat working group was tasked to deliver system-wide support for encrypted DNS that would satisfy the requirements for Zero Trust Networks. The latest bits landed in Fedora 42. (At this time installation support is present only in current Rawhide, future Fedora 43). While the generic idea is similar to what systemd-resolved does – it runs a local caching DNS resolver that accepts local unencrypted queries and forwards them over an encrypted channel to the upstream DNS servers. At this time systemd-resolved remains controversial and there is not much development activity. Therefore, after discussion with systemd developers, we decided to rely on a different service – unbound. However, we do plan to implement support for systemd-resolved in the future and give users a choice.

### Enable DoT during system runtime

Encrypted DNS is fully integrated within NetworkManager using its new dnsconfd DNS plugin. This plugin talks to dnsconfd service, which provides a D-Bus API to configure a local DNS resolver. Only unbound is supported at the moment, but more backends will be added in the future. Dedicating the DNS configuration to a standalone service helps NetworkManager focus solely on obtaining the settings. This leaves the peculiarities of individual DNS backends to be dealt with inside dnsconfd.

#### Install Required Packages

Only the dnsconfd package needs to be installed as NetworkManager is already installed in Fedora by default. This package will also pull in dependencies such as unbound.

```

    $ sudo dnf install dnsconfd
    $ sudo systemctl enable --now dnsconfd

```

#### Configure NetworkManager

The next step is to configure the NetworkManager. The following snippet sets the server to Cloudflare’s 1.1.1.1 and mode to exclusive. This means that this and only this server will be used for all connections.

```

    $ cat /etc/NetworkManager/conf.d/global-dot.conf
    [main]
    dns=dnsconfd

    [global-dns]
    resolve-mode=exclusive

    [global-dns-domain-*]
    servers=dns+tls://1.1.1.1#one.one.one.one

    $ sudo systemctl restart NetworkManager

```

#### Installing custom CA certificate

Some DNS servers require a custom CA certificate bundle which can be installed into the default location _/etc/pki/dns/extracted/pem/tls-ca-bundle.pem_. Note that the dnsconfd service requires restart as well, if this file is changed.

```

    $ cat /etc/NetworkManager/conf.d/global-dot.conf
    [main]
    dns=dnsconfd

    [global-dns]
    resolve-mode=exclusive

    [global-dns-domain-*]
    servers=dns+tls://10.0.0.100#custom.dns.example

    $ cat <<EOF > /etc/pki/dns/extracted/pem/tls-ca-bundle.pem
    ----BEGIN CERTIFICATE-----
    … custom.dns.example CA certificate
    -----END CERTIFICATE-----
    EOF

    $ sudo systemctl restart dnsconfd
    $ sudo systemctl restart NetworkManager

```

### Enable DoT during system boot time

In order to enable encrypted DNS during system boot time, it is necessary to configure the initram DNS using specific kernel arguments and install the dnsconfd-dracut package. After this the initram image must be regenerated.

#### Install Required Packages

```

    # dnf install dnsconfd-dracut

```

#### Set kernel arguments

```

    # Select DoT DNS server
    KERNELARGS="rd.net.dns=dns+tls://1.1.1.1#one.one.one.one"

    # Only our DoT server will be used for all connections
    KERNELARGS+=" rd.net.dns-resolve-mode=exclusive"

    # Use dnsconfd NetworkManager plugin
    KERNELARGS+=" rd.net.dns-backend=dnsconfd"

    # Update kernel arguments
    grubby --args "$KERNELARGS" --update-kernel 0

```

#### Regenerate the initram image

The initram image can be regenerated with various tools (like dracut), but simply reinstalling the current kernel package is the simplest solution. It will make certain that dnsconfd and any custom CA certificates are included in the image.

```

    # dnf reinstall kernel-core

```

However, note that this will regenerate initram only for the latest kernel. If an older kernel is required, it is recommended to call dracut directly and pass the desired kernel in its command line arguments.

```

    # dracut -f --kver="$KERNEL_VERSION"

```

### Enable DoT for system installation

It is possible to enable encrypted DNS during system installation in the current Fedora Rawhide (43). The only thing that is required is to pass additional kernel arguments to the installer. The installer will take care of everything and encrypted DNS will be configured for the system installation. The configuration will also be installed on the system so it will be automatically set up for the installed system as well as for the boot process. The arguments are the same as described in “Enable DoT during system boot time”, that is:

```

    … rd.net.dns=dns+tls://1.1.1.1#one.one.one.one rd.net.dns-resolve-mode=exclusive rd.net.dns-backend=dnsconfd"

```

If required, a custom CA certificate bundle can be installed with a new _%certificate_ kickstart directive.

```

    %certificate --dir /etc/pki/dns/extracted/pem/ --filename tls-ca-bundle.pem
    -----BEGIN CERTIFICATE-----
    ... custom CA certificate
    -----END CERTIFICATE-----
    %end

```

### Enable DoT in FreeIPA

FreeIPA is an open source centralized Identity Management solution that provides its own integrated DNS service. As of Fedora 42, it supports encrypted DNS as well. This is either in a strict mode, where non-encrypted DNS is completely disabled or in a relaxed mode, where both encrypted and non-encrypted protocols are allowed.

For certificate management, Administrators can either provide their own TLS certificates or allow FreeIPA to issue and manage them via its [Custodia][4] subsystem. This flexibility enables seamless integration into both enterprise-managed and automated deployments.

#### Install Required Packages

The integration of DoT into FreeIPA focuses on new deployments and encapsulates the encrypted DNS functionality in dedicated subpackages. These packages are _freeipa-client-encrypted-dns_ and _freeipa-server-encrypted-dns_. This modular approach ensures that existing installations remain unaffected unless these components are explicitly installed.

```

    $ sudo dnf install freeipa-server-encrypted-dns freeipa-client-encrypted-dns

```

#### Fresh installation

To set up FreeIPA with DoT on Fedora, simply install, deploy, and use FreeIPA as usual, but include the relevant encrypted DNS parameters when deploying. This applies to servers, replicas, and clients alike. The new functionality integrates seamlessly into standard installation workflows for new environments.

As mentioned before, administrators can either provide their own TLS certificates or allow FreeIPA to issue and manage them via its [Custodia][4] subsystem.

**Using your own certificates:**

For testing purposes, you can generate certificates using openssl.

```

    $ openssl req -newkey rsa:2048 -nodes -keyout /etc/pki/tls/certs/privkey.pem -x509 -days 36500 -out /etc/pki/tls/certs/certificate.pem -subj "/C=US/ST=NRW/L=Earth/O=CompanyName/OU=IT/CN=master.ipa.test/emailAddress=email@example.com" && chown named:named /etc/pki/tls/certs/privkey.pem /etc/pki/tls/certs/certificate.pem

```

Use this generated certificate, as shown below, when deploying FreeIPA server by using _–dns-over-tls-cert_ and _–dns-over-tls-key_ , respectively. If these options are empty, a new certificate will be requested from IPA CA.

```

    $ sudo ipa-server-install \
             --setup-dns \
             --dns-over-tls \
             --no-dnssec-validation \
             --dot-forwarder "1.1.1.1#one.one.one.one" \
             --auto-reverse \
             --domain ipa.test \
             --realm IPA.TEST \
             --hostname master.ipa.test \
             --dns-over-tls-cert /etc/pki/tls/certs/certificate.pem \
             --dns-over-tls-key /etc/pki/tls/certs/privkey.pem \
             -p Secret123 -a Secret123 -U

```

#### Existing installations

For existing deployments, administrators must take explicit action to enable DoT. This involves upgrading and installing the required packages ( _freeipa-client-encrypted-dns_ and _freeipa-server-encrypted-dns_ ). After that the ipa-dns-install commands are issued to include the encrypted DNS options. Care should be taken to evaluate the environment and ensure compatibility before enabling the new functionality.

```

    $ sudo ipa-dns-install --dns-over-tls --dot-forwarder "1.1.1.1#one.one.one.one"

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/enabling-system-wide-dns-over-tls/

作者：[Pavel BřezinaFrancisco Trivino Garcia][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/pbrezina/https://fedoramagazine.org/author/ftrivino/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/04/Enabling_DNS_TLS-816x345.jpg
[2]: https://unsplash.com/@dchris?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-black-typewriter-with-many-buttons-QmT9u2Em5VA?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://custodia.readthedocs.io/en/latest/readme.html
