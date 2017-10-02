helper functions
================

you can find useful helper functions in `libdevuansdk/zlibs/helpers`. they are
intended to help you with writing wrappers, as well as making my job easier
within developing libdevuansdk. some of these functions are required for
libdevuansdk to properly work as well.


## build_image_dist()  
this function is kind of a wrapper function, mostly used in `arm-sdk` to build a
complete "dd-able" image from start to end. to run, it requires `$arch`,
`$size`, `$parted_type`, `$bootfs`, `$workdir`, and `$strapdir` to be declared. as well as
`$parted_root`, `$parted_boot` if `$parted_type=dos`, or `$gpt_root`,
`$gpt_boot` if `$parted_type=gpt`. see `creating_wrappers(7)` for insight on
these variables.

the workflow of this function is bootstrapping a complete rootfs, creating a raw
image, installing/compiling a kernel, rsyncing everything to the raw image, and
finally, compressing the raw image.


## devprocsys()  
this function is a simple helper function that takes two arguments: `watdo` and
`werdo`. it mounts or umounts `/sys`, `/dev`, `/dev/pts`, and `procfs` where you
tell it to. for example:

```
devprocsys mount $strapdir
devprocsys umount $strapdir
```


## findloopmapp()  
this functions takes the raw image and finds a free loopdevice for it to be
mounted. it calls `losetup(8)` and `kpartx(8)`.


## qemu_install_user()  
helper function to install the userspace qemu to `$strapdir`.


## dpkgdivert()  
this one takes two arguments, `watdo` and `werdo` (much like `devprocsys`). it
will create a dpkg diversion in the place you tell it to and remove invoke-rc.d
so that apt doesn't autostart daemons when they are installed.


## enablessh()  
this function will allow root login with password in the bootstrapped rootfs.


## chroot-script()  
allows you to chroot inside the `$strapdir` and execute the
script/binary that's given to it.
takes an optional argument: `-d` (will call dpkgdivert on and off)


## silly()  
a funny function printing out random messages.
