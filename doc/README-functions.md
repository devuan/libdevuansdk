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

## img_mkimage() ##
Uses dd to dump zeroes into a raw .img of the preconfigured size.

## img_partimage_dos() ##
Partitions the raw image into dos format and formats (boot=ext2; root=ext4)

## img_partimage_gpt() ##
Partitions the raw image into gpt format and formats (boot=ext2; root=ext4)

## img_mountimage() ##
Mounts the root and boot partitions in `$workdir/rootp` in order to work on it.

## img_umountimage() ##
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

## mountdevproc()
Mounts `/dev`, `/dev/pts`, and `/proc` where needed. Takes one argument, which
is the path containing those. ex:

```
mountdevproc /path/to/bootstrapped/chroot
```

## umountdevproc()
Does the opposite of `mountdevproc`.

## silly()
Because NSA

# zlibs/sysconf
NOTE: everything is printed to stdout. Pipe or redirect if you want to write on
storage.

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

