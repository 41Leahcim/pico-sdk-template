cmake_minimum_required(VERSION 3.13)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

# The name of the project
project(my_project)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# Executable name and source files
add_executable(hello_world
    hello_world.c
)

pico_enable_stdio_usb(hello_world 1)
pico_enable_stdio_uart(hello_world 0)

# Add pico_stdlib library which aggregates commonly used features
target_link_libraries(hello_world pico_stdlib)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(hello_world)
