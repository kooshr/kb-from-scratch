cmake_minimum_required(VERSION 3.13)

set(PICO_BOARD pico2 CACHE STRING "Target Raspberry Pi Pico board")

include(pico-sdk/external/pico_sdk_import.cmake)

project(kb_from_scratch C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

pico_sdk_init()

add_executable(kb_from_scratch
    src/main.cpp
)

target_link_libraries(kb_from_scratch pico_stdlib)

# Start with the onboard LED only. USB is added with the serial/keyboard milestones.
pico_enable_stdio_usb(kb_from_scratch 0)
pico_enable_stdio_uart(kb_from_scratch 0)
pico_add_extra_outputs(kb_from_scratch)
