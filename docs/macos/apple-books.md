# Apple Books

## Prerequisites

### Disable Syncing

1. Open Apple Books
2. Under `Books` > `Preferences...` > `General`
    - Un-check `Sync: Sync collections, bookmarks, and highlights across devices`

### Disable and clear iCloud Drive

1. Open `System Preferences` > `iCloud`
    1. Un-check `iCloud Drive`
    2. Click `Manage...` at the bottom of the page
    3. Select `Books`
    4. Click `Delete Documents and Data`
2. Restart

## What to Archive

!!! warning "WIP:HIGH"

```console
~/Library/Containers/com.apple.BK*
~/Library/Containers/com.apple.iBooksX*
```

```console
$ find ~/Library/Containers -type d -name "*Books*"
./com.apple.BKAgentService/Data/Documents/iBooks
./com.apple.BKAgentService/Data/Documents/iBooks/Books
./com.apple.iBooksX
./com.apple.iBooksX/Data/Documents/BCCloudKit-iBooks
./com.apple.iBooksX/Data/Documents/BCCloudAsset-iBooks
./com.apple.iBooksX/Data/Documents/BKBookstore
./com.apple.iBooksX/Data/Library/Caches/com.apple.iBooksX
./com.apple.iBooksX.CacheDelete
./com.apple.iBooksX.DiskSpaceEfficiency
./com.apple.iBooksX.SharingExtension
./com.apple.iBooksX-SecureUserDefaults
```

```console
$ find ~/Library/Containers/com.apple.BKAgentService -type f \
    -a -exec grep -l --exclude=\*.{htm,html,xhtml} [USERNAME] {} +
.../.com.apple.containermanagerd.metadata.plist
.../Container.plist
.../Data/Documents/iBooks/Books/Books.plist
```

```console
$ find ~/Library/Containers/com.apple.iBooksX* -type f \
    -a -exec grep -l --exclude=\*.{htm,html,xhtml} [USERNAME] {} +
.../com.apple.iBooksX/.com.apple.containermanagerd.metadata.plist
.../com.apple.iBooksX/Container.plist
.../com.apple.iBooksX/Data/Documents/BKLibrary/BKLibrary-1-091020131601.sqlite-wal
.../com.apple.iBooksX/Data/Documents/BKLibrary/BKLibrary-1-091020131601.sqlite
.../com.apple.iBooksX-SecureUserDefaults/.com.apple.containermanagerd.metadata.plist
.../com.apple.iBooksX-SecureUserDefaults/Container.plist
.../com.apple.iBooksX.CacheDelete/.com.apple.containermanagerd.metadata.plist
.../com.apple.iBooksX.CacheDelete/Container.plist
.../com.apple.iBooksX.DiskSpaceEfficiency/.com.apple.containermanagerd.metadata.plist
.../com.apple.iBooksX.DiskSpaceEfficiency/Container.plist
.../com.apple.iBooksX.SharingExtension/.com.apple.containermanagerd.metadata.plist
.../com.apple.iBooksX.SharingExtension/Container.plist
```
