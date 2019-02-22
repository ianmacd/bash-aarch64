# GNU Bourne Again SHell for AArch64

## Description

[Bash](https://www.gnu.org/software/bash/) is the GNU Project's shell. Bash is
the Bourne Again SHell. Bash is an sh-compatible shell that incorporates
useful features from the Korn shell (ksh) and C shell (csh). It is intended to
conform to the IEEE POSIX P1003.2/ISO 9945.2 Shell and Tools standard. It
offers functional improvements over sh for both programming and interactive
use. In addition, most sh scripts can be run by Bash without modification.

The improvements offered by Bash include:

* Command line editing
* Unlimited size command history
* Job Control
* Shell Functions and Aliases
* Indexed arrays of unlimited size
* Integer arithmetic in any base from two to sixty-four

This Magisk module provides a statically compiled, stripped binary for the
AArch64 platform in `/system/bin/bash`.

In the context of Android, Bash offers a superior alternative to both the
standard [MirBSD Korn Shell](http://www.mirbsd.org/main.htm) (mksh) installed
with the operating system, and the ash-like shell provided by
[BusyBox](https://busybox.net).

## Building the module

Building the module from source is unnecessary, but quite easy once the proper
[toolchain](https://releases.linaro.org/components/toolchain/binaries/latest-7/aarch64-linux-gnu/)
has been installed. It goes something like this:

```shell
cd bash_source_dir  # wherever you have untarred the latest bash
prefix=$PWD/system
[ ! -d $prefix ] && mkdir $prefix
./configure --host=aarch64-linux-gnu --enable-static-link --without-bash-malloc --enable-largefile --enable-alias --enable-history --prefix=$prefix
make
aarch64-linux-gnu-strip bash
```

A `build_bash` script is provided. Edit as needed.

## Changelog

2019-02-24: v1.0

- Initial release (bash 5.0.2).
- Built with gcc 7.4.1 20181213 (linaro-7.4.1-2019.02).

## Credits

I am indebted to Brian Fox and Chet Ramey for creating and maintaining Bash,
without whose ubiquity my career in UNIX system administration would have been
considerably more tedious.
