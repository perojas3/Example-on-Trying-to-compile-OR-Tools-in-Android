cmake_minimum_required(VERSION 3.22.1)

project("myapplication" VERSION 1.0 LANGUAGES CXX)

set(BUILD_DEPS ON)
set(__PORTABLE_PLATFORM__)
set(CMAKE_CROSSCOMPILING)
include(FetchContent)
FetchContent_Declare(
        or-tools
        GIT_REPOSITORY https://github.com/google/or-tools.git
        GIT_TAG        v9.7
)
FetchContent_MakeAvailable(or-tools)

add_library(${CMAKE_PROJECT_NAME} SHARED
        native-lib.cpp)

target_link_libraries(${CMAKE_PROJECT_NAME}
        android
        log
        ortools::ortools)