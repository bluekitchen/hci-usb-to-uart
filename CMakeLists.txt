cmake_minimum_required(VERSION 3.13)

set(PROJECT hci-usb-to-uart)

include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

project(${PROJECT} C CXX)

pico_sdk_init()
add_executable(${PROJECT})

target_sources(${PROJECT} PUBLIC ${CMAKE_CURRENT_LIST_DIR}/src/main.c)

target_include_directories(${PROJECT} PRIVATE src)

target_link_libraries(${PROJECT} PUBLIC pico_stdlib tinyusb_host tinyusb_board pico_unique_id)

pico_add_extra_outputs(${PROJECT})

pico_enable_stdio_rtt(${PROJECT}  1)
pico_enable_stdio_uart(${PROJECT} 0)
