configuration
=============

much of the `libdevuansdk` configuration is done in `libdevuansdk/config`. here
you can edit the defaults if you wish to do something your needs are expressing.

## config file

`vars` and `arrs` are global arrays holding other global variables and arrays.
this is required for `zuper` and helps a lot with debugging. if you declare new
variables or arrays, add them to `vars` and `arrs`, respectively.

* `os`  
  holds the name of the distro being worked on.

* `release`  
  holds the release name of the distro. used for apt repos mostly.

* `version`  
  current version of the distro being worked on.

* `mirror`  
  a mirror holding the packages for `debootstrap`.

* `section`  
  sections of the repo. for adding in `/etc/apt/sources.list`. separate them
  with whitespaces.

* `image_name`  
  output name of the raw image. if you declare `device_name`, it will be added.
  `arm-sdk` does this.

* `core_packages`  
  this array holds the core packages that will be installed in the bootstrap
  process.

* `base_packages`  
  this array holds the base packages that will be installed later in the
  bootstrap process.

* `purge_packages`  
  this array holds the packages that will get purged at the end of the bootstrap
  process.


## overriding things

to be able to override specific unwanted functions of libdevuansdk, consider
sourcing it earlier in the process of initialization.

it is possible to override default variables, or even functions without the need
of editing libdevuansdk. share a patch with me if you wish :)
