# Game Programming in C++ Code
This repository contains the source code for *Game Programming in C++* by Sanjay Madhav.

The source code for the chapters is released under the BSD 3-clause
license. See LICENSE for more detail. Note that this license does not apply to
the code in the External directory. Each External project is licensed separately.

# Building the Code
Each chapter's code is tested and works on both Microsoft Windows and Apple macOS.

To compile on Windows, install Microsoft Visual Studio 2017 Community
(https://www.visualstudio.com/downloads/). During installation, select the
"Game Development in C++" workflow. In each Chapter directory, there is a
corresponding ChapterXX-windows.sln file to open.

To compile on macOS, install Xcode from the App Store. Each chapter has
a corresponding ChapterXX-mac.xcodeproj file.

Code for Chapter 7 and beyond uses the FMOD API for audio. This requires
a separate installation from (https://www.fmod.com/download). Download
and install version 1.09.x of the FMOD Studio API (newer versions are untested).
On Windows, install FMOD to the default directory. On Mac, copy the contents
of the FMOD package into External/FMOD.

# PostScript of the Forker
## Requirements For Arch Linux
### Chap1 and beyond
```
sudo pacman -S sdl2 sdl2_gfx sdl2_image sdl2_mixer sdl2_net sdl2_ttf
```

### Chap5 and beyond
```
sudo pacman -S SOIL glfw-x11 glew
```
NOTE: if you use wayland instead of X, you might install `glfw-wayland` and `glew-wayland`, not `glfw-x11` and `glew`

### Chap6 and beyond
```
sudo pacman -S rapidjson
```

### Chap7 and beyond
1. Download ver1.09.21 `fmodstudioapi` for Linux from https://www.fmod.com/download.
2. Extract the downloaded file `fmodstudioapi10921linux.tar.gz`, like
```
tar -xzf fmodstudioapi10921linux.tar.gz
```
Then you would get the directory named fmodstudioapi10921linux in the current directory.

3. 

```
mv fmodstudioapi10921linux {path to the repository directory}
```

NOTE: When you build the codes, you may see some error codes like 
```
/usr/bin/ld: fmodstudioapi10921linux/api/lowlevel/lib/x86_64/libfmod.so: .dynsym local symbol at index 2 (>= sh_info of 2)
```
.

These messages are warnings.

Refer to https://stackoverflow.com/questions/59915966/unknown-gcc-linker-error-but-builds-sucessfully 

## How to Execute The Programs
Run after you move to ChapterXX directory,
```
make run
```
, or
```
make run_release
```
if you want to build them in release mode.


## Remarks
1. Unnecessary libraries may be included in each makefile in ChapterXX.

This fork is for my study.

2. The Chapter12 and 13 programs can be built and run, but can not be performed properly in my environment.  

The Chapter13 and 14 programs might not be able to be run depending on your machine.
In fact, my laptop machine could run neither of the programs because they failed to create g-buffer,
but my desktop one with higher spec can run both and the Chapter14 program is performed maybe perfectly while the Chapter13 one is ill-performed.
