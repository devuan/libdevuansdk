libdevuansdk
============

libdevuansdk is a shell script library intended to unify the use and
creation of various functions spread throughout Devuan's various SDKs.

## Requirements

Devuan's SDKs are designed to be used interactively from a terminal, as
well as from shell scripts. libdevuansdk uses the functionality of the
[zuper](https://github.com/dyne/zuper) zsh library, but it does not include
it. You are required to include it in your SDK. However, libdevuansdk
requires the following packages to be installed:

```
zsh sudo cgpt parted xz-utils
```

## Documentation

Find documentation inside the `docs` directory of libdevuansdk. The following
packages need to be installed to compile the documentation:

```
python-markdown ruby-ronn
```
