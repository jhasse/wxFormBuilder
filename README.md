# wxFormBuilder [![Build status](https://ci.appveyor.com/api/projects/status/yxpn19g0st7l9r8x?svg=true)](https://ci.appveyor.com/project/jhasse/wxformbuilder-461d5)

## Download Binaries

### Windows
* wxWidgets 3.0 32-bit [Download](https://ci.appveyor.com/api/projects/jhasse/wxformbuilder-461d5/artifacts/wxFormBuilder_win32.zip?branch=master) (last successful build)

## Install From Source

### Windows (MSYS2)

Install [MSYS2](http://msys2.github.io/) and run the following inside a MinGW 32 bit shell:

```sh
pacman -S --needed mingw-w64-i686-wxWidgets git make mingw-w64-i686-binutils mingw-w64-i686-gcc mingw-w64-i686-boost
git clone --recursive --depth=1 https://github.com/wxFormBuilder/wxFormBuilder
cd wxFormBuilder
cmd.exe /C "create_build_files4.bat --wx-root=/mingw32/bin --force-wx-config --disable-mediactrl"
ln -s /mingw32/include/binutils/bfd.h /mingw32/include/bfd.h
ln -s /mingw32/include/binutils/symcat.h /mingw32/include/symcat.h
ln -s /mingw32/lib/binutils/libbfd.a /mingw32/lib/libbfd.a
ln -s /mingw32/lib/binutils/libiberty.a /mingw32/lib/libiberty.a
cd build/3.0/gmake
sed 's!\$(LDFLAGS) \$(RESOURCES) \$(ARCH) \$(LIBS)!\$(LIBS) \$(LDFLAGS) \$(RESOURCES) \$(ARCH)!g' *.make -i
sed 's!-lbfd!-lbfd -lz!g' *.make -i
make config=release
```

Run:

```sh
cd ../../../output/
./wxFormBuilder.exe
```

### Linux

Pre-requisites for Ubuntu:

```sh
sudo apt-get install libwxgtk3.0-0 libwxgtk3.0-dev libwxgtk-media3.0-dev libboost-dev
```

Download and build:

```sh
git clone --recursive --depth=1 https://github.com/wxFormBuilder/wxFormBuilder
cd wxFormBuilder
./create_build_files4.sh
cd build/3.0/gmake
make config=release
```

Run:

```sh
cd ../../../output/bin/
./wxformbuilder
```
