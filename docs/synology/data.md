# Data

## Setup a Data Scrubbing Schedule

Data scrubbing is only supported for `Shared Folders` with `Enable data checksum for advanced data integrity` enabled.

!!! quote

    To protect a shared folder with CRC32 checksum and copy-on-write strategies, you can enable data checksum for advanced data integrity during the shared folder's creation. CRC32 checksum is applied to checking if the data remain identical to when they were originally written, and the system will automatically use RAID redundancy to fix corrupted data. Copy-on-write helps to improve data consistency upon abnormal system shutdown.

    [Create a Shared Folder | Synology](https://www.synology.com/en-global/knowledgebase/DSM/help/DSM/AdminCenter/file_share_create)

!!! quote

    [The `Enable data checksum for advanced data integrity`] checkbox enables metadata redundancy on BTRFS that will allow you to recover from bit rot. There is no good reason not to enable it. Performance overhead is minimal and not nearly a bottleneck in any meaningful scenario.

    For image data, where single bit flip can ruin the image it’s a must. This feature is in fact one of the benefits of using BTRFS as a filesystem.

    via [r/synology](https://www.reddit.com/r/synology/comments/c600jq/enable_data_checksum_for_advanced_data_integrity/es5b8nw/)

:octicons-location-24: Where

`Storage Manager` • `Storage Pool`

:octicons-question-24: How

- In the `Data Scrubbing` tab
    - Click `Set Schedule`
    1. In the `Time Session` tab
       - Check `Enable Data Scrubbing schedule`
         1. Set `Frequency` to `Repeat every three months`
         2. Set a `Start date`
         3. Under `Time Session`
            - Select `Run at all times`
    2. In the `Select Target` tab
       - Select Storage Pools

## Setup Storage Analyzer

Install `Storage Analyzer` from `Package Center`

:octicons-location-24: Where

`Storage Analyzer`

:octicons-question-24: How

1. Set a location for saving reports if one has not already been set. _Note that this can easily be changed at a later date._
2. Under `Report Profile`
   - Click `Create` and follow the wizard to create a report.

## Clean Recycle Bin Task

:octicons-location-24: Where

`Control Panel` • `Task Scheduler`

:octicons-question-24: How

- Click `Create` select `Scheduled Task` then `Recycle Bin`
    - In the `Create task` window
        1. In the `General` tab
            - Under `General Settings`
                - Set `Task` to `Clean Recycle Bin`
        2. In the `Schedule` tab
            1. Under `Date`
                - Set `Run on the following days` to `Daily`
            2. Under `Time`
                1. Set `First run time` to `00:00`
                2. Set `Frequency` to `Every day`
                3. Set `Last run time` to `00:00`
        3. In the `Task Settings` tab
            1. Under `Empty Recycle Bins`
                - Select `Empty all Recycle Bins`
            2. Under `Retention Policy`
                - Select and set `Number of days to retain deleted files` to `30`

## Disable HDD Hibernation

:octicons-location-24: Where

`Control Panel` • `Hardware & Power`

:octicons-question-24: How

- In the `HDD Hibernation` tab
    1. Under `The internal hard disk(s) and the external SATA disk will hibernate...`
        - Set `Time` to `none`
    1. Under `USB hard disks will hibernate...`
        - Set `Time` to `none`

## Setup Snapshots

Install `Snapshot Replication` from `Package Center`

:octicons-location-24: Where

`Snapshot Replication` • `Snapshots`

:octicons-question-24: How

- In the `Shared Folder` tab
    1. Select a shared folder
    1. Click `Settings`
        - In the `Settings` window
            1. In the `Schedule` tab
                - Check `Enable snapshot schedule`
                    1. Set `Select days` to `Daily`
                    2. Set `Starting at` to `00:00`
                    3. Set `Frequency` to `Every hour`
                    4. Set `Repeat until` to `23:00`
            2. In the `Retention` tab
                1. Select `Advanced retention rules`
                2. Click `Configure`
                    - In the `Configure` window
                        1. Set `24` for `hourly snapshots (One snapshot per hour)`
                        2. Set `7` for `daily snapshots (One snapshot per day)`
                        3. Set `2` for `weekly snapshots (One snapshot per week)`
                        4. Set `1` for `monthly snapshots (One snapshot per month)`
                        5. Set `1` for `yearly snapshots (One snapshot per year)`
            3. In the `Advanced` tab
                - Check `Make snapshot visible`

## Setup Time Machine

### Create a Shared Folder

:octicons-location-24: Where

`Control Panel` • `Shared Folder`

:octicons-question-24: How

- Click `Create` > `Create`
    - In the `Shared Folder Creation Wizard`
        1. Under `Set up basic information`
            1. Set `Name` to `TimeMachine`
            2. Check `Hide this shared folder in "My Network Places"`
            3. Uncheck `Enable Recycle Bin`
        2. Under `Configure advanced settings`
            1. Check `Enable data checksum for advanced data integrity`
            2. Check `Enable shared folder quota`
                - Set the quota to 2-3x the size of the source drive.

### Enable Bonjour SMB Broadcast

:octicons-location-24: Where

`Control Panel` • `File Services`

:octicons-question-24: How

- In the `SMB/AFP/NFS` tab
    - Under `SMB`
        - Check `Enable SMB service`
- In the `Advanced` tab
    - Under `Bonjour`
    1. Check `Enable Bonjour Time Machine broadcast via SMB`
    2. Click `Set Time Machine Folders` and select `TimeMachine`.

### Enable Time Machine Backups

:octicons-location-24: Where

`macOS` • `System Preferences` • `Time Machine`

:octicons-question-24: How

1. Click `Select Backup Disk...`
    1. Select `TimeMachine`
    2. Check `Encrypt backups`
    3. Click `Use Disk`
    4. When prompted:
        1. Enter and verify a password
        2. Click `Encrypt Disk`
2. Additionally:
    1. Check `Back Up Automatically`
    2. Check `Show Time Machine in menu bar`

## Hyper Backup

!!! warning "TODO"
