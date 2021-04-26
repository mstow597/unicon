Unicon
======

Unicon is a very high level programming language. It runs on many operating systems
including most Linux distributions, Windows, macOS, and BSD systems. It also supports
most modern CPU architectures such as i386, amd64, armhf, arm64, and ppc64el.


Installation
------------
The latest sources are available from Unicon's git repositories on Sourceforge and GitHub.
To get the sources from either repo do:

```
git clone https://github.com/uniconproject/unicon.git

```
or

```
git clone git://git.code.sf.net/p/unicon/unicon
```

`git` is available on linux via the standard package managers, for example on a Debian system

```
sudo apt install git
```
On macOS git is available with xcode. On windows you can install and setup git using the instructions:
[here](http://unicon.org/git.html)

For source tarballs and binary distributions, see unicon.org
[download page](http://unicon.org/downloads.html)


Build Instructions
------------------

_Prerequisites_
- Gnu/Unix utilities such as shell, make, grep, etc.
- C language compiler that supports C99 such as gcc or clang

The initial configuration is done via a standard GNU autoconf script, run:
```
./configure --help
```
For configuration options help. On Windows:
```
sh configure --help
```

The configuration script allows you to enable or disable features in the Unicon build at compile time.
Some of the features are turned on by default as long as the dependecies are satisfied. Those features
can be turned off by doing `--disable-FEATURE`, for example:
```
./configure --disable-graphics
```
disables all graphics support. On the other hand, some features are disabled by default. Those can
be turned on by doing `--enable-FEATURE`, for example, to enable operator overloading:
```
--configure --enable-ovld
```
On other aspect to consider is that the configure script is opporuntitic when it comes to turning on features.
Features that are enabled by default will be disabled automatically if they are missing dependencies. If you want
to change the behavior to make the configure script stop instead of skipping a feature when its dependcies are
missing, just enable that feature explicitly. For example, if you want to enable https/ssl, do:
```
./configure --enable-ssl
```
If openssl development library is not present on the system, the configre script will stop with an error message:
```
configure: error: "ssl requires libssl-dev or equivalent"
```

### Linux
Use the package manager in your Linux distribution to get a build utilities and C compiler.
For example, on a Debian system
```
sudo apt install build-essential
```
Go into the Unicon directory and run:
```
./configure
make
```
After that you can add `unicon/bin` to the $PATH environment variable or install Unicon instead:
```
make install
```

### macOS
Install Xcode command line tools (or all of Xcode) from the macOS app store.
After that the build steps are the same as those on Linux. To ensure using clang,
explicitly set the compiler as follows:

```
./configure CC=clang CXX=clang++
```

### Windows

- Download and run [mingw-get-setup.exe](https://sourceforge.net/projects/mingw/files/Installer/)

   Go through the install process and  use it to install only msys-base. This will give you an MSYS (not MSYS2)
   environment with all the needed Linux/gnu utils.

- Get MinGW64 compiler suite, [TDM package](https://jmeubank.github.io/tdm-gcc/) is known to work with Unicon.
Most recent package is [9.2.0](https://jmeubank.github.io/tdm-gcc/articles/2020-03/9.2.0-release)

Note that you maybe missing the tool "make". TDM MinGW comes with a "make" that is named mingw32-make.exe.
That file can be found under the insallation directory of MinGW64 inside the bin directory.
create a copy of that file and name it "make.exe" before continuing.

After that you can use the standard Windows command line `cmd` terminal to build Unicon.
```
sh configure
```
or
```
make WUnicon64
```
Which is a shortcut for running:
```
sh configure --build=x86_64-w64-mingw32
```
The option `x86_64-w64-mingw32` ensures the build is 64-bit. After the script finishes do:
```
make
```

Help
----

Questions and comments to: jeffery@unicon.org

