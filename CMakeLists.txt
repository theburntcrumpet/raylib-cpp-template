cmake_minimum_required(VERSION 3.10)
project(Algos)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "-Wall")

find_package(GTest CONFIG REQUIRED)
find_package(raylib REQUIRED)

# Include directories
include_directories(${PROJECT_SOURCE_DIR}/include)

# Source files
set(SOURCES
    ${PROJECT_SOURCE_DIR}/src/main.cxx
)

set(TEST_SOURCES
    ${PROJECT_SOURCE_DIR}/src/test/tests_main.cxx
)

# Build Game

add_executable(game ${SOURCES})
target_link_libraries(
  game
  raylib
)

enable_testing()

# Add executable
add_executable(tests ${TEST_SOURCES})

target_link_libraries(
  tests
  GTest::gtest_main
  raylib
)

include(GoogleTest)
gtest_discover_tests(tests)
