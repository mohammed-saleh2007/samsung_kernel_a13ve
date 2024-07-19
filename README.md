#Linux kernel
============

There are several guides for kernel developers and users. These guides can
be rendered in a number of formats, like HTML and PDF. Please read
Documentation/admin-guide/README.rst first.

In order to build the documentation, use ``make htmldocs`` or
``make pdfdocs``.  The formatted documentation can also be read online at:

    https://www.kernel.org/doc/html/latest/

There are various text files in the Documentation/ subdirectory,
several of them using the Restructured Text markup notation.
See Documentation/00-INDEX for a list of what is contained in each file.

Please read the Documentation/process/changes.rst file, as it contains the
requirements for building and running the kernel, and information about
the problems which may result by upgrading your kernel.

1. How to Build
- get Toolchain
From android git server, codesourcery and etc ..
`- clang/host/linux-x86/clang-r383902/bin/aarch64-linux-gnu-`
- edit Makefile
edit `"CROSS_COMPILE"` to right toolchain path(You downloaded).

EX)  `CROSS_COMPILE=<android platform directory you download>/android/prebuilts/clang/host/linux-x86/clang-r383902/bin/aarch64-linux-gnu-`

EX)  `CROSS_COMPILE=/usr/local/toolchain/clang/host/linux-x86/clang-r383902/bin/aarch64-linux-gnu-`
// check the location of toolchain
edit "CLANG" to right path(You downloaded).

EX)   `CC=<android platform directory you download>/android/prebuilts/clang/host/linux-x86/clang-r383902/bin/clang`

EX)  `CC=/usr/local/toolchain/clang/host/linux-x86/clang-r383902/bin/clang`
// check the location of toolchain
edit "CLANG_TRIPLE" to right path(You downloaded).

EX) `CLANG_TRIPLE=<android platform directory you download>/android/prebuilts/aarch64-linux-gnu-`

EX) `CLANG_TRIPLE=/usr/local/toolchain/aarch64-linux-gnu-` 
// check the location of toolchain
- to Build
```
$ export ANDROID_MAJOR_VERSION=r
$ export ARCH=arm64
$ make -C $(pwd) O=$(pwd)/out KCFLAGS=-w CONFIG_SECTION_MISMATCH_WARN_ONLY=y a13ve_defconfig
$ make -C $(pwd) O=$(pwd)/out KCFLAGS=-w CONFIG_SECTION_MISMATCH_WARN_ONLY=y
```
2. Output files
```
- Kernel : arch/arm64/boot/Image.gz
- module : drivers/*/*.ko
```

3. How to Clean
```
$ make clean
```