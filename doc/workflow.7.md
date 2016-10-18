libdevuansdk workflow
=====================

Working with libdevuansdk splits into categories of what you want to do.
`zlibs` are files separated into these "categories":

## bootstrap

Contains the functions for the bootstrap process. Creating a minimal debootstrap
base, and making it into a tarball for later use so you don't have to wait for
the debootstrap on every build.

## helpers

Contains the helper functions for libdevuansdk that make your and my life a bit
easier.

## imaging

Contains the functions necessary for creating raw dd-able images.

## kernel

Contains the functions for installing a vanilla kernel.

## rsync

Contains rsync functions

## sysconf

Contains the default system configuration.
