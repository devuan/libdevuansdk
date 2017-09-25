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

## Notes

To support the development, you are welcome to open issues on problems and
bugs you encounter. Open merge requests of patches or simply get involved
in other tasks evident on <https://git.devuan.org>

## Acknowledgments

Devuan's SDK was originally conceived during a period of residency at the
Schumacher college in Dartington, UK. Greatly inspired by the laborious and
mindful atmosphere of its wonderful premises.

The Devuan SDK is Copyright (c) 2015-2017 by the Dyne.org Foundation

Devuan SDK components are designed, written and maintained by:

- Ivan J. <parazyd@dyne.org>
- Denis Roio <jaromil@dyne.org>
- Enzo Nicosia <katolaz@freaknet.org>

This source code is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option)
any later version.

This software is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for
more details.

You should have received a copy of the GNU General Public License along
with this source code. If not, see <http://www.gnu.org/licenses/>.
