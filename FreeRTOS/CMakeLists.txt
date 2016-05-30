# CMake minimum version
cmake_minimum_required (VERSION 3.1)

# Project Infomation
project (STM32F7xx_FreeRTOSLib)

# Reset output path
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/lib)

# Set include path
include_directories (../Drivers/CMSIS/Include )
include_directories (../Drivers/CMSIS/Device/Include )
include_directories (../Drivers/STM32F7xx_HAL_Driver/Inc)
include_directories(Include)

# The need build source path and build all files
aux_source_directory (Source DIR_STM32F7xx_FreeRTOS_SRCS)

# CC AR
set(CMAKE_C_COMPILER "arm-none-eabi-gcc")
set(CMAKE_C_AR "arm-none-eabi-ar")

# CFLAGS
set (CMAKE_C_FLAGS "-g -mthumb -fno-builtin -mcpu=cortex-m7 -mfpu=fpv5-sp-d16 -mfloat-abi=softfp -Wall -std=gnu99 -ffunction-sections -fdata-sections -fomit-frame-pointer -mabi=aapcs -fno-unroll-loops -ffast-math -ftree-vectorize" CACHE INTERNAL "c compiler flags")
set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DSTM32F746xx -DUSE_HAL_DRIVER")

# Generate the target to the static library
add_library (STM32F7xx_FreeRTOS ${DIR_STM32F7xx_FreeRTOS_SRCS})

# Make clean-all
add_custom_target (clean-all COMMAND rm -rf ${CMAKE_BINARY_DIR}/*)
