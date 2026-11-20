add_executable(kb_from_scratch
    src/main.cpp
)

target_link_libraries(kb_from_scratch pico_stdlib)

# Start with the onboard LED only. USB is added with the serial/keyboard milestones.
pico_enable_stdio_usb(kb_from_scratch 0)
pico_enable_stdio_uart(kb_from_scratch 0)
pico_add_extra_outputs(kb_from_scratch)
