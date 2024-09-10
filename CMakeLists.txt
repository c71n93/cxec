cmake_minimum_required(VERSION 3.26)
project(cxec)

set(CMAKE_CXX_STANDARD 20)

include_directories(include)

add_subdirectory(test)

add_executable(cxec
    src/main.cpp
)

# Setting up clang-tidy and clang-format

find_program(CLANG_TIDY_EXE NAMES "clang-tidy" REQUIRED)
set(CLANG_TIDY_COMMAND "${CLANG_TIDY_EXE}")
set_target_properties(cxec PROPERTIES CXX_CLANG_TIDY "${CLANG_TIDY_COMMAND}")

file(GLOB_RECURSE
        ALL_CXX_SOURCE_FILES
        *.[chi]pp *.[chi]xx *.cc *.hh *.ii *.[CHI]
)
find_program(CLANG_FORMAT "clang-format")
if(CLANG_FORMAT)
    add_custom_target(
        clang-format
        COMMAND ${CLANG_FORMAT}
        -i
        -style=file
        ${ALL_CXX_SOURCE_FILES}
    )
endif()
