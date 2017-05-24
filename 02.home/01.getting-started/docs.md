---
title: 'Getting Started'
taxonomy:
    category:
        - docs
---
# Setting up Mimic

Currently, Mimic runs on Linux (ARM & Intel architectures), Mac OSX, and Windows. It has been untested on Android, and we have plans to make it available on iOS. 

## Supported platforms

- Linux (ARM & Intel architectures)
- Mac OS X
- Windows

**Untested**
- Android

**Future**
- iOS

## Requirements

This is the list of requirements. Below there is the commands needed on the most popular distributions and supported OS.

- A good C compiler:
  * Linux or Mac OSX: _Recommended:_ gcc or clang
  * Windows: _Recommended:_ GCC under [Cygwin](https://cygwin.com/) or [mingw32](http://www.mingw.org/)
- GNU make, automake and libtool
- pkg-config
- ICU library and headers
- An audio engine:
  * Linux: ALSA/PortAudio/PulseAudio (_Recommended:_ ALSA)
  * Mac OSX: PortAudio
  * Windows: PortAudio

## Install Dependencies

#### Linux 

##### On Debian/Ubuntu
```
$ sudo apt-get install gcc make pkg-config automake libtool libicu-dev libasound2-dev
```

##### On Fedora
```
$ sudo dnf install gcc make pkgconfig automake libtool libicu-devel alsa-lib-devel
```

##### On Arch
```
$ sudo pacman -S --needed install gcc make pkg-config automake libtool icu alsa-lib
```

#### Mac OSX

- Install *Brew*
  ```
  $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  ```

- Install *pkg-config*, *automake*, *libtool*, *icu* and *PortAudio*
  ```
  $ brew install pkg-config automake libtool portaudio icu4c
  ```

### Windows

#### Cross compiling:

The fastest and most straightforward way to build mimic for windows is by
cross-compilation from linux. This requires some additional packages to be
installed.

On Ubuntu 16.04 (xenial):
```
sudo apt-get install gcc make pkg-config automake libtool libicu-dev wine binutils-mingw-w64-i686 mingw-w64-i686-dev gcc-mingw-w64-i686 g++-mingw-w64-i686

```

On Ubuntu 14.04 (trusty):

```
sudo apt-get install gcc make pkg-config automake libtool libicu-dev mingw32 mingw32-runtime wine
```

#### Native Windows building

- Audio device and audio libraries are optional, as mimic can write its output to a waveform file.
- Some of the source files are quite large, that some C compilers might choke on these. So, *gcc* is recommended.
- Visual C++ 6.0 is known to fail on the large diphone database files
- The build process is **MUCH** slower on Windows.


Read the next page for instructions on installation.
