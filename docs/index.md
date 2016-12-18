index
=====

`libdevuansdk` is a shell script library intended to unify the use and creation
of various functions spread throughout devuan's various sdks.

devuan's sdks are designed to be used interactively from a terminal, as
well as from shell scripts. libdevuansdk uses the functionality of the
[zuper](https://github.com/dyne/zuper) zsh library, but it does not include
it. you are required to include it in your sdk. however, `libdevuansdk`
requires the following packages to be installed:

```
zsh debootstrap sudo kpartx cgpt xz-utils
```

## notes

to support the development, you are welcome to open issues on problems and
bugs you encounter. open merge requests of patches or simply get involved
in other tasks evident on <https://git.devuan.org>

## toc

* [workflow](workflow.7.html)
* [libdevuansdk configuration](configuration.7.html)
* [libdevuansdk helper functions](helper_functions.7.html)
* [creating wrappers around libdevuansdk](creating_wrappers.7.html)

