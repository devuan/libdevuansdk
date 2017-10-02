creating wrappers around libdevuansdk
=====================================

libdevuansdk holds all the helper functions you might need, but it does not
allow you to simply use it in a completely automated fashion. for that you
will have to wrap some zsh around libdevuansdk.

there are a few mandatory variables that you are required to declare before
sourcing libdevuansdk. otherwise libdevuansdk might write to some places of the
system you wouldn't want to.

## requirements

before sourcing it, libdevuansdk assumes you already loaded and initialized
the [zuper](https://github.com/dyne/zuper) zsh library.


### mandatory variables

* `$R`  
  the root directory of your wrapper. in almost every situation you can set
  it as `$PWD`

* `$workdir`  
  the working directory of the current "build". a sane default is
  `$R/tmp/workdir`

* `$strapdir`  
   the bootstrap directory of the current "build". it holds the rootfs when
   you debootstrap. sane default: `$workdir/rootfs`

* `$arch`  
  the CPU architecture of the current "build". values like: `amd64`, `i386`,
  `armhf`, etc...


### Optional variables

* `$extra_packages`  
  this should hold an array of packages that exist in the devuan package tree.
  they will get installed as a part of the bootstrap process.

* `$purge_packages`  
  this is an array that holds a list of packages that will get removed at the
  final steps of the bootstrap process. note that this array is not empty by
  default, so you should only add to it in your wrapper, not override it. 
  just to be safe.

* `$size`  
  This variable will hold the value in MiB for `dd` to know how many zeroes it
  should put in the raw image.  
  ex: `size=1337`

* `$parted_type`  
  if you are creating a raw (dd-able) image, this variable will tell
  libdevuansdk how to partition that image. either `dos` or `gpt`.

* `$parted_boot`  
  used if `$parted_type=dos`. it holds the values for `parted` and the
  formatting of the `boot` partition.  
  ex: `parted_boot="fat32 2048s 264191s"`.  
  see the `image_partition_raw_dos()` function in `libdevuansdk/zlibs/imaging`
  for a better understanding on how the variable is used.

* `$parted_root`  
  used if `$parted_type=dos`. it holds the values for `parted` and the
  formatting of the `root` partition.  
  ex: `parted_root="ext4 264192s 100%"`.  
  see the `image_partition_raw_dos()` function in `libdevuansdk/zlibs/imaging`
  for a better understanding on how the variable is used.

* `$gpt_boot`  
  used if `$parted_type=gpt`. it is an array holding the start and end values
  for partitioning the `boot` partition.  
  ex: `gpt_boot=(8192 32768)`  
  see the `image_partition_raw_gpt()` function in `libdevuansdk/zlibs/imaging
  for a better understanding on how the variable is used.

* `$gpt_root`  
  used if `$parted_type=gpt`. it is an array holding the start value for
  partitioning the `root` partition.  
  ex: `gpt_root=(40960)`  
  currently libdevuansdk chooses this as a startpoint, and maxes out remaining
  available space. again, see the `image_partition_raw_gpt()` function for a
  better understanding.

* `$bootfs`
  This variable controls the file system type of the boot partition. Recognised
  values are `none`, `vfat` (or the synonyms `fat` and `dos`), and `ext4`.
  When `none` is specified, the boot partition is left raw and not mounted,
  so /boot becomes part of the root partition.

* `$qemu_bin`  
  declare this if you are bootstrapping for an architecture different than
  yours. it should hold the path to `qemu-user-static` or a similarly named
  statically compiled qemu for userspace.
