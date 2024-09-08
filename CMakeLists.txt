cmake_minimum_required(VERSION 3.26)
project(cxec)

set(CMAKE_CXX_STANDARD 20)

add_subdirectory(test)

add_executable(cxec
    src/main.cpp
)
