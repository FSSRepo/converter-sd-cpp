cmake_minimum_required(VERSION 3.12)
project("convert-sd-cpp")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if (NOT XCODE AND NOT MSVC AND NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
    set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release" "MinSizeRel" "RelWithDebInfo")
endif()

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
    set(SD_STANDALONE ON)
else()
    set(SD_STANDALONE OFF)
endif()

set(CONVERT_APP convert)

add_executable(${CONVERT_APP} convert.cpp)

add_subdirectory(ggml)
add_subdirectory(thirdparty)

target_link_libraries(${CONVERT_APP} PUBLIC ggml zip)
target_include_directories(${CONVERT_APP} PUBLIC . thirdparty)
target_compile_features(${CONVERT_APP} PUBLIC cxx_std_11)
