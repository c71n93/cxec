include(FetchContent)
FetchContent_Declare(
        googletest
        URL https://github.com/google/googletest/archive/b514bdc898e2951020cbdca1304b75f5950d1f59.zip # release 1.15.2
)
FetchContent_MakeAvailable(googletest)
enable_testing()

function(cxec_test SOURCE_NAME)
    get_filename_component(TARGET_NAME ${SOURCE_NAME} NAME_WE)
    add_executable(
            ${TARGET_NAME}
            ${SOURCE_NAME}
    )
    target_link_libraries(
            ${TARGET_NAME}
            GTest::gtest_main
    )
    include(GoogleTest)
    gtest_discover_tests(${TARGET_NAME})
endfunction(cxec_test)

cxec_test(dummy_test.cpp)
