# Network

## Set a Local Static IP Address

!!! info "DHCP Server"

    Before proceeding, make sure to have setup your router's [DHCP Server](../01-router/#setup-dhcp-server). Otherwise the assigned IP address could be given to another device.

:octicons-location-24: Where

`Control Panel` • `Network`

:octicons-question-24: How

- In the `Network Interface` tab
    - Select `[Network Interface]` and click `Edit`
        - In the `IPv4` tab
            1. Select `Use manual Configuration`
            2. Set `IP address` to `192.168.[X].[XXX]`

## Disable QuickConnect

:octicons-location-24: Where

`Control Panel` • `QuickConnect`

:octicons-question-24: How

- In the `General` tab
    - Uncheck `Enable QuickConnect`

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

## Change Default DSM Ports

:octicons-location-24: Where

`Control Panel` • `Network`

:octicons-question-24: How

- In the `DSM Settings` tab
    - Under `General`
        - Under `DMS ports`
            1. Set `HTTP` to `[XXXX]`
            2. Set `HTTPS` to `[XXXX]`

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

## Auto-mount SMB on macOS

!!! note "TODO:LOW"

<!-- https://stackoverflow.com/questions/18145509/automount-samba-folder-on-mac -->
<!-- https://gist.github.com/rudelm/7bcc905ab748ab9879ea -->
<!-- https://apple.stackexchange.com/questions/697/how-can-i-mount-an-smb-share-from-the-command-line -->

## Connect via SSH

:octicons-location-24: Where

`Control Panel` • `Terminal & SNMP`

:octicons-question-24: How

- In the `Terminal` tab
    1. Check `Enable SSH service`
    2. Optionally[^ssh], change `Port` to an unused number between `1024` and `65535`[^ports].
    3. If Synology's firewall is enabled, make sure to add a rule to allow access to the port.

[^ssh]: This might or might not be a good idea. [Why putting SSH on another port than 22 is bad idea](https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/).
[^ports]: See [Common Network Ports & Protocols](./reference.md#common-network-ports-protocols)

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

!!! note "TODO:LOW"

<!-- https://flatpacklinux.com/2020/01/07/configure-the-ssh-server-on-your-synology-nas/ -->

## Connect via the Internet

!!! warning "TODO:HIGH"

Although this guide has many steps, the two most important ones are setting up the **DDNS Service** and **Port Forwarding**. These two will provide immediate, albeit un-secured (and possibly inconvenient) access to the Synology via the internet. The additional steps alleviate these issues.

### Setup DDNS with `synology.me`

### Add SSL Certificate via Let's Encrypt

### Setup Application Portals (Optional)

### Setup Connection via Port Forwarding

### Setup Connection via Reverse Proxy

#### Setup Synology Firewall

#### Setup Port Forwarding

|             Address             | Incoming Port |     Redirect to IP     | with Port |
| :------------------------------ | :-----------: | :--------------------- | :-------: |
| `http://sub-domain.domain.com`  |      80       | 192.168.X.XXX[^nas-ip] |    80     |
| `https://sub-domain.domain.com` |      443      | 192.168.X.XXX[^nas-ip] |    443    |

### Setup Connection via VPN

<!-- <https://www.wundertech.net/synology-nas-openvpn-server-setup-configuration/> -->

#### Setup OpenVPN

#### Setup Synology Firewall

#### Setup Port Forwarding

| Incoming Port |     Redirect to IP     | with Port |
| :-----------: | :--------------------: | :-------: |
|     1194      | 192.168.X.XXX[^nas-ip] |   1194    |

#### Configure Clients

[^nas-ip]: This is the local Static IP Address of the Synology. If the Synology does not have a Static IP address, please see [Set a Static IP Address](#set-a-static-ip-address).

## Firewall

!!! warning "TODO:LOW"

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
