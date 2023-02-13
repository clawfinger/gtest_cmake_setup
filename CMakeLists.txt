cmake_minimum_required(VERSION 3.14)
set(CMAKE_CXX_STANDARD 14)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

project(test_env LANGUAGES CXX)

set(HEADERS
    test.h
)
set(SOURCES
    test.cpp
)

enable_testing()

add_executable(test_env
    ${HEADERS}
    ${SOURCES}
    )

target_link_libraries(
  test_env
  GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(test_env)