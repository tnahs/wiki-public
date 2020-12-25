# Synology Network

## Set a Static IP Address

!!! info "DHCP Server"

    Before proceeding, make sure to have setup your router's [DHCP Server](../01-router/#setup-dhcp-server). Otherwise the assigned IP address could possibly be given out by your router to another device.

:octicons-location-24: Where

`Control Panel` • `Network`

:octicons-question-24: How

- In the `Network Interface` tab
    - Select `[Network Interface]` and click `Edit`
        - In the `IPv4` tab
            1. Select `Use manual Configuration`
            2. Set `IP address` to `192.168.0.[XXX]`

## Disable admin/guest Accounts

:octicons-location-24: Where

`Control Panel` • `User`

:octicons-question-24: How

- In the `User` tab
    - Select `[Username]` and click `Edit`
        - In the `Info` tab
            - Check `Disable this account`
                - Select `Immediately`

## Disable QuickConnect

:octicons-location-24: Where

`Control Panel` • `QuickConnect`

:octicons-question-24: How

- In the `General` tab
    - Uncheck `Enable QuickConnect`

## Auto-update DSM

:octicons-location-24: Where

`Control Panel` • `Update & Restore`

:octicons-question-24: How

- In the `DSM Update` tab
    - Click `Update Settings`
        1. Select `Automatically install the new update`
        2. Set `Check schedule` to `Daily` at `00:00`

## Change Default DSM Ports

:octicons-location-24: Where

`Control Panel` • `Network`

:octicons-question-24: How

- In the `DSM Settings` tab
    - Under `General`
        - Under `DMS ports`
            1. Set `HTTP` to `[XXX0]`
            2. Set `HTTPS` to `[XXX1]`

## Enable DoS protection

:octicons-location-24: Where

`Control Panel` • `Security`

:octicons-question-24: How

- In the `Protection` tab
    1. Select `[Network Interface]`
    2. Check `Enable DoS protection`

## Enable Auto Block & Account Protection

:octicons-location-24: Where

`Control Panel` • `Security`

:octicons-question-24: How

- In the `Account` tab
    1. Under `Auto Block`
        - Check `Enable auto block`
            1. Set `Login attempts` to `10`
            2. Set `Within (minutes)` to `5`
    2. Under `Account Protection`
        - Check `Enable Account Protection`
            1. Set `Login attempts` to `10`
            2. Set `Within (minutes)` to `1`
            3. Set `Cancel account protection (minutes later)` to `30`

## Keep admin Password on Reset

:octicons-location-24: Where

`Control Panel` • `Update & Restore`

:octicons-question-24: How

- In the `Reset` tab
    - Under `Reset Option`
        - Check `Keep your admin password unchanged`

## Enable SMB

:octicons-location-24: Where

`Control Panel` • `File Services`

:octicons-question-24: How

- In the `SMB/AFP/NFS` tab
    1. Under `SMB`
        - Check `Enable SMB service`
    2. Under `AFP`
        - Uncheck `Enable AFP service`
    3. Under `NFS`
        - Uncheck `Enable NFS`

## Setup Security Advisor

:octicons-location-24: Where

`Security Advisor`

:octicons-question-24: How

- In the `Advanced` menu
    1. Under `Security Baseline`
        - Select `For home and personal use`
    2. Under `Scan Schedule`
        1. Check `Enable regular scan schedule`
        2. Set `Run on the following days` to `Daily`
        3. Set `Run task` to `00:00`

## Email Notifications

:octicons-location-24: Where

`Control Panel` • `Notification`

:octicons-question-24: How

1. In the `Push Service` tab
    1. Check `Send notifications regarding system status via Synology's email server`.
    2. Set `Recipients` to desired email address(es).
    3. Verify email address(es).
2. In the `Advanced` tab
    - Select critical `Events`.

        |                           Event                           |        Email        |
        | :-------------------------------------------------------- | :-----------------: |
        | **External Storage**                                      |                     |
        | External device was not ejected properly                  | :octicons-check-24: |
        | USB disk failed                                           | :octicons-check-24: |
        | **Power Supply**                                          |                     |
        | UPS disconnected                                          | :octicons-check-24: |
        | UPS has returned to AC mode                               | :octicons-check-24: |
        | UPS has entered battery mode                              | :octicons-check-24: |
        | UPS low battery reached                                   | :octicons-check-24: |
        | **Security Advisor**                                      |                     |
        | Security Risks Found                                      | :octicons-check-24: |
        | Malware Detected                                          | :octicons-check-24: |
        | **Internal Storage**                                      |                     |
        | Volume in extremely low capacity <10%>                    | :octicons-check-24: |
        | Volume in low capacity <20%>                              | :octicons-check-24: |
        | Alert of drive with read abnormality (UNC error)          | :octicons-check-24: |
        | Drive in critical status                                  | :octicons-check-24: |
        | Drive is failing                                          | :octicons-check-24: |
        | Bad sectors on drive increased                            | :octicons-check-24: |
        | Drive in warning status                                   | :octicons-check-24: |
        | Drive temperature is not within the operating temperature | :octicons-check-24: |
        | Drive I/O error                                           | :octicons-check-24: |
        | **System**                                                |                     |
        | System abnormality detected                               | :octicons-check-24: |
        | Improper shutdown                                         | :octicons-check-24: |
        | Disk overheating shutdown                                 | :octicons-check-24: |
        | GPU overheating shutdown                                  | :octicons-check-24: |
        | System overheating shutdown                               | :octicons-check-24: |
        | Account Protected                                         | :octicons-check-24: |
        | System storage space crashed                              | :octicons-check-24: |
        | File system error                                         | :octicons-check-24: |
        | Checksum mismatch                                         | :octicons-check-24: |
        | IP Conflict                                               | :octicons-check-24: |

## SSH

!!! note "WIP"

:octicons-location-24: Where

`Control Panel` • `Terminal & SNMP`

:octicons-question-24: How

- In the `Terminal` tab
    1. Check `Enable SSH service`
    2. Optionally[^ssh], change `Port` to an unused number between `1024` and `65535`[^ports].
    3. If Synology's firewall is enabled, make sure to add a rule to allow access to the port.

[^ssh]: This might or might not be a good idea. [Why putting SSH on another port than 22 is bad idea](https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/).
[^ports]: See [Common Network Ports & Protocols](./06-reference.md#common-network-ports-protocols)

It's now possible to connect to the filesystem via the `ssh` command from the terminal.

``` console
$ ssh [NAS_USERNAME]@[NAS_IP_ADDRESS]
```

Use `-p` for a custom ssh port.

``` console
$ ssh [NAS_USERNAME]@[NAS_IP_ADDRESS] -p [PORT]
```

### Login via Password

Connect via `ssh`

```console
$ ssh user@192.168.1.111
```

If this is the first login attempt, confirm the connection by typing `yes`. Note the highlighted line. The `list of known hosts` is easily accessible/editable. See below.

```console hl_lines="4"
The authenticity of host '192.168.1.111 (192.168.1.111)' can't be established.
ECDSA key fingerprint is SHA256:███████████████████████████████████████████.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '192.168.1.111' (ECDSA) to the list of known hosts.
```

Enter the password for the username on the NAS.

```console
user@92.168.1.111's password: ████████████████...
user@NAS:/$
```

The `list of known hosts` are located in the `known_hosts` file in `~/.ssh`.

``` console
$ cat ~/.ssh/known_hosts
192.168.1.111 ecdsa-sha2-nistp256 ████████████████...
```

### Login via SSH Key

!!! note "TODO"

## Firewall

!!! note "WIP"

:octicons-location-24: Where

`Control Panel` • `Security`

:octicons-question-24: How

- In the `Firewall` tab
    - Under `General`
        - Check `Enable firewall`
    - Under `Firewall Profile`
        - Select `default` and click `Edit Rules`

|       Enabled       |            Ports            |   Protocol   | Source IP |   Action   |
| :-----------------: | :-------------------------: | :----------: | :-------: | :--------: |
| :octicons-check-24: | Management UI, File Station |     TCP      |    All    |   Allow    |
| :octicons-check-24: |     Windows file server     |     All      |    All    |   Allow    |
| :octicons-check-24: |           Bonjour           |     UDP      |    All    |   Allow    |
| :octicons-check-24: |    `[Additional Ports]`     | `[Protocol]` |  `[IP]`   | `[Action]` |
| :octicons-check-24: |             All             |     All      |    All    |    Deny    |

## SSL Certificate

!!! note "TODO"

## VPN

!!! note "TODO"

<!-- <https://www.wundertech.net/synology-nas-openvpn-server-setup-configuration/> -->
