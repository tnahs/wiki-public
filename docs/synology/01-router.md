# Router

## Setup DHCP Server

:octicons-location-24: Where

Check your router for specifics.

:octicons-question-24: How

- Enable `DHCP Server`
    - Set Start: `192.168.X.2`
    - Set End: `192.168.X.100`

## Setup DHCP Address Reservation

!!! note "TODO"

## Port Forwarding

!!! note "TODO"

<!-- <https://www.tp-link.com/us/support/faq/72/> -->

## Disable UPnP

:octicons-location-24: Where

Check your router for specifics.

:octicons-question-24: How

Check your router for specifics.

## (Optional) Set Custom DNS Server

!!! quote

    1.1.1.1 is a public DNS resolver operated by Cloudflare that offers a fast and private way to browse the Internet. Unlike most DNS resolvers, 1.1.1.1 does not sell user data to advertisers. In addition, 1.1.1.1 has been measured to be the fastest DNS resolver available.

    [What is 1.1.1.1? - Cloudflare](https://www.cloudflare.com/learning/dns/what-is-1.1.1.1/)

:octicons-location-24: Where

Check your router for specifics.

:octicons-question-24: How

- Enable `Custom DSN Servers`
    1. Set `Primary DNS` to `1.1.1.1`
    2. Set `Secondary DNS` to `8.8.8.8`
