# Router

## Setup DHCP Server

:octicons-location-24: Where

Check your router for specifics.

:octicons-question-24: How

- Enable `DHCP Server`
    - Set Start: `192.168.X.2`
    - Set End: `192.168.X.100`

## Disable UPnP

:octicons-location-24: Where

Check your router for specifics.

:octicons-question-24: How

Check your router for specifics.

## 1.1.1.1 DNS Server

!!! quote

    1.1.1.1 is a public DNS resolver operated by Cloudflare that offers a fast and private way to browse the Internet. Unlike most DNS resolvers, 1.1.1.1 does not sell user data to advertisers. In addition, 1.1.1.1 has been measured to be the fastest DNS resolver available.

    [What is 1.1.1.1? - Cloudflare](https://www.cloudflare.com/learning/dns/what-is-1.1.1.1/)

!!! quote

    The addresses of 1.1.1.1 are:

    - 1.1.1.1
    - 1.0.0.1
    - 2606:4700:4700::1111
    - 2606:4700:4700::1001

    [1.1.1.1 docs](https://developers.cloudflare.com/1.1.1.1/)

!!! quote

    1.1.1.1 for Families is the easiest way to add a layer of protection to your home network, and protect it from malware and adult content. 1.1.1.1 for Families leverages Cloudflare's global network to ensure that it is fast and secure around the world, and includes the same [strong privacy guarantees](https://developers.cloudflare.com/1.1.1.1/1.1.1.1/privacy/public-dns-resolver/) that we committed to when we launched 1.1.1.1 two years ago.

    [...]

    Using the following DNS resolvers will block malicious content:

    - 1.1.1.2
    - 1.0.0.2
    - 2606:4700:4700::1112
    - 2606:4700:4700::1002

    [...]

    When you change your DNS resolvers to the addresses below, 1.1.1.1 for Families will block malware and adult content.

    - 1.1.1.3
    - 1.0.0.3
    - 2606:4700:4700::1113
    - 2606:4700:4700::1003

    [1.1.1.1 for Families - 1.1.1.1 docs](https://developers.cloudflare.com/1.1.1.1/1.1.1.1-for-families/)

:octicons-location-24: Where

Check your router for specifics.

:octicons-question-24: How

Check your router for specifics.

1. For a privacy-conscious DNS
    1. Set `Primary DNS` to `1.1.1.1`
    2. Set `Secondary DNS` to `1.0.0.1`
2. For a privacy-conscious DNS with malware-blocking
    1. Set `Primary DNS` to `1.1.1.2`
    2. Set `Secondary DNS` to `1.0.0.2`
3. For a privacy-conscious DNS with malware & adult-content blocking
    1. Set `Primary DNS` to `1.1.1.3`
    2. Set `Secondary DNS` to `1.0.0.3`
