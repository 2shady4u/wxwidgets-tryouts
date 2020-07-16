# wxwidgets-tryouts

## Build Instructions

Most of the instructions derive from [here](
https://wiki.wxwidgets.org/Compiling_wxWidgets_with_MSYS-MinGW) and I mostly repeat them to keep my own sanity in check.

## Install MinGW

Download [MinGW](http://www.mingw.org/) and install it in the recommended installation folder.

## Install MSYS2

Download [MSYS2](https://www.msys2.org/) and install it using the Windows instructions. When completed you'll have to update
the system packages with following commands:

```
pacman -Syu
pacman -Su
```

After that (you'll probably have to restart MSYS2 to complete the update), you can install some other essential packages:

```
pacman -S make automake autoconf
```

This will install the required autotools for compilation of the project.

### Compile and Install wxWidgets

Download the latest wxWidgets source code from [here](https://www.wxwidgets.org/downloads/) and extract it into the recommended
folder (`C:/wx`)

Make a new directory for building wxWidgets from scratch:

```
mkdir msw-debug
cd msw-debug
```

Run configure to configure the custom wxWidgets build in debug mode and with static flag:

```
../configure --disable-shared --enable-debug
```

Compile and install the custom build of wxWidgets:

```
make && make install
```

### Compile the project

Simply go to this project's folder and enter it. Then execute following command in the MSYS MGWin 64-bit terminal:

```
aclocal && autoreconf --install && ./configure && make
```

If there are problems regarding detection of the C++ compiler you might need to forcibly add MinGW to the path:

```
export PATH=${PATH}:/c/MinGW/bin
```
