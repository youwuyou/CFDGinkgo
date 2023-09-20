cmake_minimum_required(VERSION 3.10)

project(tutorials)

# List of example folder (add more if needed)
set(EXAMPLES_LIST
    demo-poisson-solver
    demo-heat-equation
    step01-linear-convection-1D
    # step02-nonlinear-convection-1D
    # step03-diffusion-1D
    # step04-burgers-equation-1D
    # step05-linear-convection-2D
    # step06-nonlinear-convection-2D
    # step07-diffusion-2D
    # step08-burgers-equation-2D
    # step09-laplace-equation-2D
    # step10-poisson-equation-2D
    # step11-cavity-flow-2D
    # step12-channel-flow-2D
    # Add more folders here ...
)

# Build for all examples
foreach(example ${EXAMPLES_LIST})
    add_subdirectory(${example})
endforeach()