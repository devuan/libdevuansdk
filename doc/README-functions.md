libdevuansdk functions
----------------------

# zlibs/debootstrap

## bootstrap()

Main function, goes through stages 1, 2, and 3 of debootstrap.

### bootstrap_config_cleanup() ###

Final cleanup of the rootfs.

### bootstrap_config_thirdstage() ###

Shell script for the system's third debootstrap stage.

### bootstrap_tar_pack() ###

Make a tarball of a base working system, ready to be worked on later.

### bootstrap_tar_unpack() ###

Unpack the tarball of a base working system to the strapdir.

# zlibs/imaging

## img_mkimage()
Uses dd to dump zeroes into a raw .img of the preconfigured size.
Goes further and rsyncs strapdir into the image, installs bootloader and a
kernel.

## img_partition_dos() ##
Partitions the raw image into dos format and formats (boot=ext2; root=ext4)

## img_partition_gpt() ##
Partitions the raw image into gpt format and formats (boot=ext2; root=ext4)

## img_rsync_strapdir() ##
rsyncs the strapdir to te mounted rootfs of our raw image.

## img_install_bootloader() ##
calls functions from sysconf: `conf_install_kernel` and `conf_install_grub` to
install the on the image

## img_mount() ##
Mounts the root and boot partitions in `$workdir/rootp` in order to work on it.

## img_umount() ##
Undoes the above function.

# zlibs/helpers

## escalate()
Acts as a wrapper for escalating user privilege when needed. Takes two
arguments, user and command in the style of:

```
escalate root "chroot /somewhere/where/i/want/to"
```

## findloopmapp()
For the raw image. Finds a free loopdevice and makes a /dev/mapper device which
is then kpartx-ed to give us partitions we can mount.

## mountdevprocsys()
Mounts `/sys`, `/dev`, `/dev/pts`, and `/proc` where needed. Takes one argument, which
is the path containing those. ex:

```
mountdevproc /path/to/bootstrapped/chroot
```

## umountdevprocsys()
Does the opposite of `mountdevprocsys`.

## aptautostart()
enables/disables apt to autostart services after their packages are installed.
takes args `on` or `off` as 1st argument, and `/path/to/chroot` as second
argument

## silly()
Because NSA

# zlibs/sysconf
NOTE: everything is printed to stdout. Pipe or redirect if you want to write on
storage.

## conf_install_grub()
Installs `grub-pc` to the target. Arg taken is a path to a chroot

## conf_install_kernel()
Installs `linux-image-$arch` to the target. Arg taken is a path to the chroot.

## conf_print_debconf()
Prints out the config for console-common setup

## conf_print_fstab()
Prints the fstab

## conf_print_hostname()
Prints the hostname. Requires `$os` to be declared.

## conf_print_hosts
Prints default `/etc/hosts`

## conf_print_networkifaces()
Prints the `/etc/network/interfaces` file

## conf_print_resolvconf()
Prints the `/etc/resolv.conf` file.

## conf_print_sourceslist()
Prints default `/etc/apt/sources.list`

