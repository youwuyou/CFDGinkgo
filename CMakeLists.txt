# Required minimum version of CMake
cmake_minimum_required(VERSION 3.14)

# Project name
project(CFD_Ginkgo)

# Include the custom SetupTests.cmake file
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
include(SetupDependency)

# Ginkgo v1.6.0
find_or_fetch_library("Ginkgo" "1f1ed46e724334626f016f105213c047e16bc1ae" "1.6.0" "https://github.com/ginkgo-project/ginkgo.git")

# Configuration options for setting up tests for each subdirectory
option(BUILD_BENCHMARKS "Enable Google Benchmarking" OFF)
option(BUILD_TESTS "Generate build files for unit tests" ON)
option(VISU_OPENCV "Visualization using OpenCV" ON)

# Configure Google Test v1.12.0
if(BUILD_TESTS)
    enable_testing()
    # Find and include Google Test
    find_or_fetch_library("GTest" "f8d7d77c06936315286eb55f8de22cd23c188571" "1.12.0" "https://github.com/google/googletest.git")

    # Find and include Google Test
    include(GoogleTest)  
    include(SetupTests)
endif()

# Configure Benchmark v1.8.3
if(BUILD_BENCHMARKS)
    find_or_fetch_library("Benchmark" "344117638c8ff7e239044fd0fa7085839fc03021" "1.8.3" "https://github.com/google/benchmark.git")
endif()

# Configure Visualization with OpenCV v4.6.0
if(VISU_OPENCV)
    find_or_fetch_library("OpenCV" "b0dc474160e389b9c9045da5db49d03ae17c6a6b" "4.6.0" "https://github.com/opencv/opencv.git")
endif()

# Directory containing the codes
add_subdirectory(tutorials)