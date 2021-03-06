project(kia-soul-brake)

set(ARDUINO_DEFAULT_BOARD mega2560)

generate_arduino_firmware(
    kia-soul-brake
    SRCS
    ${CMAKE_SOURCE_DIR}/common/libs/arduino_init/arduino_init.cpp
    ${CMAKE_SOURCE_DIR}/common/libs/mcp_can/mcp_can.cpp
    ${CMAKE_SOURCE_DIR}/common/libs/pid/oscc_pid.cpp
    ${CMAKE_SOURCE_DIR}/common/libs/serial/oscc_serial.cpp
    ${CMAKE_SOURCE_DIR}/common/libs/can/oscc_can.cpp
    ${CMAKE_SOURCE_DIR}/common/libs/time/oscc_time.cpp
    src/main.cpp
    src/globals.cpp
    src/accumulator.cpp
    src/helper.cpp
    src/master_cylinder.cpp
    src/brake_control.cpp
    src/communications.cpp
    src/init.cpp)

target_include_directories(
    kia-soul-brake
    PRIVATE
    include
    ${CMAKE_SOURCE_DIR}/common/include
    ${CMAKE_SOURCE_DIR}/common/libs/arduino_init
    ${CMAKE_SOURCE_DIR}/common/libs/mcp_can
    ${CMAKE_SOURCE_DIR}/common/libs/pid
    ${CMAKE_SOURCE_DIR}/common/libs/serial
    ${CMAKE_SOURCE_DIR}/common/libs/can
    ${CMAKE_SOURCE_DIR}/common/libs/time)

add_subdirectory(utils)
