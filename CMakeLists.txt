# Required minimum version of CMake
cmake_minimum_required(VERSION 3.1)

# Project name
project(CFD_Ginkgo)

# Find the installed Ginkgo library
find_package(Ginkgo 1.7.0 REQUIRED)

# Enable testing
enable_testing()

# Include the custom SetupTests.cmake file
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# Configuration options
option(BUILD_TESTS "Generate build files for unit tests" ON)

# For setting up tests for each subdirectory
if(BUILD_TESTS)
  # Configure CTest
  include(SetupTests)
endif()

# Directory containing the codes
add_subdirectory(tutorials)