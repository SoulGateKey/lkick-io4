# RP2040 IO4

## 构建
适用于Windows环境
1. 安装 MinGW 并设置环境变量（我使用的是CLion捆绑安装的MinGW 比较方便）
2. 安装 [GNU Arm Embedded Toolchain](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)  
   选择最新版本Release 找到`Windows (mingw-w64-x86_64) hosted cross toolchains`  
   `AArch32 bare-metal target (arm-none-eabi)`  
   找到像这样`arm-gnu-toolchain-??.?.rel?-mingw-w64-x86_64-arm-none-eabi.exe`的文件下载（下载可能较慢）并安装  
   ***切记 在安装完成时 勾选 `Add path to environment varible`以添加至环境变量***
2. 在你要保存代码的地方打开命令行 `git clone https://github.com/SoulGateKey/lkick-io4.git`
3. 进入代码的根目录，执行 ``git submodule update --init --recursive`` 
4. 在代码的根目录创建一个 `build`文件夹,进入 `build`文件夹
5. 如果是第一次构建执行 `cmake ..`
6. 执行 `cmake --build .`进行构建  
   注意 有可能在构建时遇到 `error: 'uint16_t' `的报错，请在 `.\pico-sdk\tools\pioasm\`的`pio_disassembler.cpp` 的第 1 行 和 `pio_siassembler.h`的第 13 行 添加 `#include <cstint>` ，然后再次进行构建
7. 如果一切正常的话，构建好的uf2文件应该在 `.\build` 目录下。 进入rp2040的bootloader模式，将uf2文件拖入RPI-RP2中即可完成烧录。
## 使用

你可以在 `stdinclude.h`中修改按键、读卡器、编码器的引脚位置  
 注意编码器使用模拟输入，你可以自行修改代码以使用其他方式输入。

## 鸣谢 

https://github.com/satorusaka/lkick-io4  
https://github.com/XxLittleCxX/lkick-io4
