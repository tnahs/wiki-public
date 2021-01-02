# Misc

## Run `sudo` Commands Without a Password

### Prerequisites

`sudo` rules can be added directly to `/etc/sudoers` or to a file placed in `/etc/sudoers.d`:

```console
$ sudo cat /etc/sudoers.d
```

```plaintext hl_lines="5"
# /etc/sudoers.d

# ...

## Read drop-in files from /private/etc/sudoers.d
## (the '#' here does not indicate a comment)
#includedir /private/etc/sudoers.d
```

!!! info

    The `#includedir` directive can be used to create a `sudo.d` directory that the system package manager can drop sudoers rules into as part of package installation.  For example, given:

    ```plaintext
    #includedir /etc/sudoers.d
    ```
    **sudo** will read each file in `/etc/sudoers.d`, skipping file names that end in ~ or contain a . character to avoid causing problems with package manager or editor temporary/backup files.  Files are parsed in sorted lexical order.  That is, `/etc/sudoers.d/01_first` will be parsed before `/etc/sudoers.d/10_second`. Be aware that because the sorting is lexical, not numeric, `/etc/sudoers.d/1_whoops` would be loaded **after** `/etc/sudoers.d/10_second`. Using a consistent number of leading zeroes in the file names can be used to avoid such problems.

    [Ubuntu Manpage: sudoers - default sudo security policy module](https://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html)

### Adding Rules

Create and edit a new file with `visudo`.

```console
$ sudo visudo -f /etc/sudoers.d/usercmds
```

!!! warning

    The `sudoers` file should **always** be edited by the **visudo** command which locks the file and does grammatical checking. It is imperative that `sudoers` be free of syntax errors since **sudo** will not run with a syntactically incorrect `sudoers` file.

    [Ubuntu Manpage: sudoers - default sudo security policy module](https://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html)

Add **sudo** rules using the following format:

```plaintext
[USER]   ALL = (ALL) NOPASSWD: [COMMAND, ...]
```

Replacing `[USER]` with the using being granted permission and `[COMMAND, ...]` with a list of comma separated commands using absolute paths e.g.:

```plaintext
# /etc/sudoers.d/usercmds

user-a ALL = (ALL) NOPASSWD: /bin/usercmd-a
user-b ALL = (ALL) NOPASSWD: /bin/usercmd-b, /bin/usercmd-b2 --flag
```

!!! info "More Info"

    By default, **sudo** requires that a user authenticate him or herself before running a command. This behavior can be modified via the NOPASSWD tag. Like a Runas_Spec, the NOPASSWD tag sets a default for the commands that follow it in the Cmnd_Spec_List. Conversely, the PASSWD tag can be used to reverse things. For example:

    ```plaintext
    ray rushmore = NOPASSWD: /bin/kill, /bin/ls, /usr/bin/lprm
    ```

    would allow the user **ray** to run `/bin/kill`, `/bin/ls`, and `/usr/bin/lprm` as **root** on the machine rushmore without authenticating himself. If we only want **ray** to be able to run `/bin/kill` without a password the entry would be:

    ```plaintext
    ray rushmore = NOPASSWD: /bin/kill, PASSWD: /bin/ls, /usr/bin/lprm
    ```
    [Ubuntu Manpage: sudoers - default sudo security policy module](https://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html)

via [How do I run specific sudo commands without a password?](https://askubuntu.com/a/159009)

## Get Command Line Tools Version

Run the following command to see the version of CLT:

```console
$ xcode-select --version
xcode-select version 2384
```

```console
$ pkgutil --pkg-info=com.apple.pkg.CLTools_Executables
package-id: com.apple.pkg.CLTools_Executables
version: 12.3.0.0.1.1607026830
volume: /
location: /
install-time: 1608921954
groups: com.apple.FindSystemFiles.pkg-group
```

## Resize Sparsebundles

To compact the image, empty the trash, un-mount it and run:

```console
$ hdiutil compact [PATH_TO_SPARSEBUNDLE]
```

To increase the image, un-mount it and run:

```console
$ hdiutil resize -size [SIZE] [PATH_TO_SPARSEBUNDLE]
```

!!! info

    For a list of size specifiers, run:

    ```console
    hdiutil resize -help
    ```

via [Resize a Sparse Bundle Image using Terminal](https://vidrih.net/2016/03/15/resize-a-sparse-bundle-image-using-terminal)

## Disable OCSP

```console
$ sudo vim /etc/hosts
```

```plaintext hl_lines="8"
# /etc/hosts

# ...

127.0.0.1       localhost
255.255.255.255 broadcasthost
::1             localhost
127.0.0.1       ocsp.apple.com
```

via [Your Computer Isn't Yours](https://sneak.berlin/20201112/your-computer-isnt-yours/>)

## Export Contacts

- In `Contacts`
    1. `Edit` > `Select All`
    2. `File` > `Export...` > `Export vCard...`
