cmake_minimum_required(VERSION 3.13)

# initialize pico-sdk from submodule
# note: this must happen before project()
include(pico-sdk/pico_sdk_init.cmake)

project(pico-serial-to-hid)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

add_executable(pico-serial-to-hid
        pico-serial-to-hid.c
        usb_descriptors.c
        )

target_include_directories(pico-serial-to-hid PRIVATE ${CMAKE_CURRENT_LIST_DIR})

target_link_libraries(pico-serial-to-hid PRIVATE pico_stdlib tinyusb_device tinyusb_board)

pico_add_extra_outputs(pico-serial-to-hid)