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

!!! note "TODO:MED"

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

## Enable Uninterruptible Power Supply (UPS) Support

:octicons-location-24: Where

`Control Panel` • `Hardware & Power`

:octicons-question-24: How

- In the `UPS` tab
    - Check `Enable UPS support`