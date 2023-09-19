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

# For setting up tests for each subdirectory
if(BUILD_TESTS)
  # Configure CTest
  include(SetupTests)
endif()


# List of example folder (add more if needed)
set(EXAMPLES_LIST
    tutorials/demo-poisson-solver
    tutorials/demo-heat-equation
    tutorials/step01-linear-convection-1D
    # tutorials/step02-nonlinear-convection-1D
    # tutorials/step03-diffusion-1D
    # tutorials/step04-burgers-equation-1D
    # tutorials/step05-linear-convection-2D
    # tutorials/step06-nonlinear-convection-2D
    # tutorials/step07-diffusion-2D
    # tutorials/step08-burgers-equation-2D
    # tutorials/step09-laplace-equation-2D
    # tutorials/step10-poisson-equation-2D
    # tutorials/step11-cavity-flow-2D
    # tutorials/step12-channel-flow-2D
    # Add more folders here ...
)

# Build for all examples
foreach(example ${EXAMPLES_LIST})
    add_subdirectory(${example})
endforeach()
