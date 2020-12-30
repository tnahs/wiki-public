# Misc

## Run `sudo` Commands Without a Password

!!! warning "WIP:HIGH"

```console
$ sudo visudo
```

Where `user` is the user to and `/path/to/executable --args` is the exact command to execute.

```plaintext hl_lines="6"
/etc/sudoers

...

root             ALL = (ALL) ALL
user ALL=(ALL) NOPASSWD:/path/to/executable --args
%admin           ALL = (ALL) ALL
```

via [How do I run specific sudo commands without a password?](https://askubuntu.com/a/159009)

## Command Line Tools

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

## Sparsebundles

A Sparse Bundle Image will increase in size automatically but will not shrink automatically.

!!! note

    Before shrinking the sparse bundle, mount it and empty the trash to get rid of any deleted items from the image.

To compact the image, un-mount it and run:

``` console
$ hdiutil compact path/to/file.sparsebundle
```

To increase the image, un-mount it and run:

``` console
$ hdiutil resize -size [size] path/to/file.sparsebundle
```

via [Resize a Sparse Bundle Image using Terminal](https://vidrih.net/2016/03/15/resize-a-sparse-bundle-image-using-terminal)

## Disable OCSP

``` console
$ sudo vim /etc/hosts
```

```plaintext hl_lines="8"
/etc/hosts

...

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
