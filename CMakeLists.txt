cmake_minimum_required(VERSION 3.26)
project(cxec)

set(CMAKE_CXX_STANDARD 20)

include_directories(include)

add_subdirectory(test)

add_executable(cxec
    src/main.cpp
)

# search for clang-tidy
find_program(CLANG_TIDY_EXE NAMES "clang-tidy" REQUIRED)
# setup clang-tidy command from executable + options
set(CLANG_TIDY_COMMAND "${CLANG_TIDY_EXE}")
# set CXX_CLANG_TIDY property after defining the target
set_target_properties(cxec PROPERTIES CXX_CLANG_TIDY "${CLANG_TIDY_COMMAND}")
