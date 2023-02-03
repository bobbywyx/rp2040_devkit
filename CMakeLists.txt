cmake_minimum_required(VERSION 3.13)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
#include(C:/Users/yixin/Documents/File/rp2040/git-pico-sdk/pico-sdk/pico_sdk_init.cmake)
#include(pico_sdk_import.cmake)

#include(pico-sdk/pico_sdk_init.cmake)

include(../pico-arduino-compat/pico_sdk_import.cmake)

add_subdirectory(C:/Users/yixin/Documents/File/rp2040/pico-arduino-compat/libs/adafruit-sh110x build-pac-sh110x)


project(rp2040)
# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

file(GLOB_RECURSE SOURCES "Src/*.*"
        "Lib/*.*"
        "Inc/*.*")

include_directories("Inc"
        "Lib/Inc")

# rest of your project
add_executable(main ${SOURCES})

# Add pico_stdlib library which aggregates commonly used features
target_link_libraries(main pico_stdlib pico_stdlib hardware_i2c pac-adafruit-sh110x)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(main)