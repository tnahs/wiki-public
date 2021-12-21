# DSM

## Auto-update DSM

:octicons-location-24: Where

`Control Panel` • `Update & Restore`

:octicons-question-24: How

- In the `DSM Update` tab
    - Click `Update Settings`
        1. Select `Automatically install the new update`
        2. Set `Check schedule` to `Daily` at `00:00`

## Disable admin/guest Accounts

:octicons-location-24: Where

`Control Panel` • `User`

:octicons-question-24: How

- In the `User` tab
    - Select `[Username]` and click `Edit`
        - In the `Info` tab
            - Check `Disable this account`
                - Select `Immediately`

## Keep admin Password on Reset

:octicons-location-24: Where

`Control Panel` • `Update & Restore`

:octicons-question-24: How

- In the `Reset` tab
    - Under `Reset Option`
        - Check `Keep your admin password unchanged`

## Setup 2FA

!!! warning "TODO"

## Setup Security Advisor

:octicons-location-24: Where

`Security Advisor`

:octicons-question-24: How

- In the `Advanced` tab
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
    - Select `Events`:

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

## Set Network Time Protocol (NTP) Server

:octicons-location-24: Where

`Control Panel` • `Regional Options`

:octicons-question-24: How

- In the `Time` tab
    - Under `Time Setting`
        1. Select `Synchronize with NTP server`
        2. Set `Server address` to `time.nist.gov`

## Enable Uninterruptible Power Supply (UPS) Support

:octicons-location-24: Where

`Control Panel` • `Hardware & Power`

:octicons-question-24: How

- In the `UPS` tab
    - Check `Enable UPS support`

## Enable SynoCommunity Packages

:octicons-location-24: Where

`Package Center`

:octicons-question-24: How

- Click `Settings`
    - In the `General` tab
        - Under `Trust Level`
            - Select `Synology Inc. and trusted publishers`
    - In the `Package Sources` tab
        - Click `Add`
            1. Set `Name` to `SynoCommunity`
            2. Set `Location` to `https://packages.synocommunity.com`
            3. Click `Ok`

A new `Community` tab should now be available in `Package Center`.

## Reset/Re-install DSM

See [How to reset my Synology NAS | Synology](https://www.synology.com/en-global/knowledgebase/DSM/tutorial/General_Setup/How_to_reset_my_Synology_NAS)

!!! quote

    After your Synology NAS has been reset, the data on the Synology NAS will remain intact. However, before you reset your Synology NAS and re-install DSM, we highly recommended you to launch the [...] the Hyper Backup package [...] on your DSM, so as to back up your data and system configuration settings in case unexpected data loss occurs.

    [How to reset my Synology NAS | Synology](https://www.synology.com/en-global/knowledgebase/DSM/tutorial/General_Setup/How_to_reset_my_Synology_NAS)
