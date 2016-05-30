# STM32F7 FreeRTOS blinky on linux

### By wangxian
---
**Note:** Use the GNU/Make with arm-none-eabi-gcc and cmake tools.

### Steps
1. CMake the FreeRTOS and compiler to the static library.
  * Go into the project and go into the FreeRTOS directory.
  * `cd FreeRTOS/Build`
  * `cmake ..`
  * `make` to generate the `libSTM32F7xx_FreeRTOS.a`

2. Check that `libSTM32F7xx_HAL_Drivers.a` file in the Drivers/Build/lib/ , if not in the folder then:
  * `cd Drivers/Build`
  * `cmake ..`
  * `make`

3. Compiler the user source
  * `cd Build`
  * `cmake ..`
  * `make`
  * that could generate the blinky.bin and blinky.hex files

4. Plug your stm32f7 board into your PC, and make sure you got the  st-link tools, if you didn't have the tools, you can go to the site [ST-LINKV1/V2](https://github.com/texane/stlink) to download the tools.

5. Go into the Build/bin/
    * `make flash`
    * you can see the program writing the flash

6. Here wo go. let's conquer the STM32F7!

### I'm the green hand.So Sorry for that bad english.
