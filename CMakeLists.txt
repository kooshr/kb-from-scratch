cmake_minimum_required(VERSION 3.13)

set(PICO_BOARD pico2 CACHE STRING "Target Raspberry Pi Pico board")

include(pico-sdk/external/pico_sdk_import.cmake)

project(kb_from_scratch C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

pico_sdk_init()

add_subdirectory(firmware)
