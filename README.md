# Simulator project for LVGL embedded GUI Library

The [LVGL](https://github.com/lvgl/lvgl) is written mainly for microcontrollers and embedded systems, however you can run the library **on your PC** as well without any embedded hardware. The code written on PC can be simply copied when your are using an embedded system.

This project is configured for [VSCode](https://code.visualstudio.com) and only tested on Linux, although this may work on OSx or WSL. It requires a working version of GCC, GDB and make in your path.

To allow debugging inside VSCode you will also require a GDB [extension](https://marketplace.visualstudio.com/items?itemName=webfreak.debug) or other suitable debugger. All the requirements, build and debug settings have been pre-configured in the [.workspace](simulator.code-workspace) file.

The project can use **SDL** but it can be easily relaced by any other built-in LVGL dirvers.

## Get started

### Get the PC project
Clone the PC project and the related sub modules:

```bash
git clone --recursive https://github.com/lvgl/lv_port_pc_vscode
```

### Install SDL and build tools
You can download SDL from https://www.libsdl.org/

#### Linux 
Copy this in the Terminal:
```bash
sudo apt-get update && sudo apt-get install -y build-essential libsdl2-dev cmake
```

## Usage

### Visual Studio Code
1. Be sure you have installed [SDL and the build tools](#install-sdl-and-build-tools)
1. Open the project by double clicking on `simulator.code-workspace` or opening it with `File/Open Workspace from File`
2. Install the recommended plugins
3. Click the Run and Debug page on the left, and select `Debug LVGL demo with gdb` from the drop-down on the top. Like this:
![image](https://github.com/lvgl/lv_port_pc_vscode/assets/7599318/f527b235-5718-4949-b5f0-bd807b3a64ba)
4. Click the Play button or hit F5 to start debugging.

### CMake
This project uses CMake under the hood which can be used without Visula Studio Code too. Just type these in a Terminal when you are in the project's root folder:
```bash
mkdir build
cd build
cmake ..
make -j
```




## Optional library

There are also FreeType and FFmpeg support. You can install these according to the followings:

### Linux
```bash
# FreeType support
wget https://kumisystems.dl.sourceforge.net/project/freetype/freetype2/2.13.2/freetype-2.13.2.tar.xz
tar -xf freetype-2.13.2.tar.xz
cd freetype-2.13.2
make
make install
```

```bash
# FFmpeg support
git clone https://git.ffmpeg.org/ffmpeg.git ffmpeg
cd ffmpeg
git checkout release/6.0
./configure --disable-all --disable-autodetect --disable-podpages --disable-asm --enable-avcodec --enable-avformat --enable-decoders --enable-encoders --enable-demuxers --enable-parsers --enable-protocol='file' --enable-swscale --enable-zlib
make
sudo make install
```

<!-- mac终端命令编译运行 -->
``` bash

https://blog.csdn.net/weixin_39510813/article/details/139271684


brew install sdl2
brew install cmake

//可能需要 root 权限运行相关命令
git clone https://github.com/lvgl/lv_port_pc_vscode.git
rmdir lvgl
git clone https://github.com/lvgl/lvgl.git
git status
git checkout 8691574
mkdir build
cd build
cmake ..
make
../bin/main
```
