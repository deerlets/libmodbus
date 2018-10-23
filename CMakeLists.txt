cmake_minimum_required(VERSION 3.11)
project(libmodbus C)

set(CMAKE_C_STANDARD 11)

include_directories(src)
if (WIN32)
    include_directories(src/win32)
endif ()

add_library(modbus SHARED
        src/modbus-data.c
        src/modbus-private.h
        src/modbus-rtu-private.h
        src/modbus-rtu.c
        src/modbus-rtu.h
        src/modbus-tcp-private.h
        src/modbus-tcp.c
        src/modbus-tcp.h
        src/modbus.c
        src/modbus.h)

target_link_libraries(modbus zio)
if (WIN32)
    target_link_libraries(modbus ws2_32)
endif ()