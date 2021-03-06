cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

project(logdevice-prometheus)

include(GNUInstallDirs)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
list(APPEND CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -fno-new-ttp-matching")
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_THREAD_PREFER_PTHREAD ON)
set(PLUGIN_DIR "${CMAKE_CURRENT_SOURCE_DIR}")
set(PLUGIN_STAGING_DIR "${CMAKE_BINARY_DIR}/staging")

# Setting Output
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

find_package (glog)
find_package(Threads REQUIRED)

set(UNIT_TEST_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/test)

include(build-prometheus-cpp)
include(build-gtest)
include(build-logdevice)

enable_testing()

add_subdirectory(src)
