# CFDGinkgo

## Introduction

This tutorial series aims to create hands-on examples for beginners to learn how to utilize the Ginkgo library. We draw inspiration from the popular CFD Python tutorial, specifically the module titled [CFD Python: 12 steps to Navier-Stokes](https://lorenabarba.com/blog/cfd-python-12-steps-to-navier-stokes/) taught by Prof. Lorena Barba at Boston University. Our goal is to illustrate the framework and capabilities of the Ginkgo library by adapting and expanding upon the concepts presented in the CFDPython tutorial.

## Structure

```bash
CFDGinkgo
├── cmake                 # .cmake files for build system
├── CMakeLists.txt
├── README.md
└── tutorials             # demo codes for the tutorial 
    ├── demo-XX            
    └── stepXX-XX-1D/2D
```

## Getting Started

In this tutorial series, we assume you have already built and installed the Ginkgo library as a prerequisite. If you have not yet done it, please refer to the tutorial for [installing Ginkgo](https://github.com/ginkgo-project/ginkgo/wiki/Tutorial-1:-Getting-Started). In case you encounter any problems with building Ginkgo, you can refer to the [discussions section](https://github.com/ginkgo-project/ginkgo/discussions) for help.

Once you have Ginkgo installed in your system, now you can open a UNIX terminal and go to a dedicated directory where you want this tutorial series to locate at. Then issue the following command

```bash
git clone git@github.com:youwuyou/CFDGinkgo.git
```

This will create a subdirectory CFDGinkgo containing codes and other data needed for the tutorial examples.

Now we create a build directory and initialize the build system. By default, we compile the repository with tests, you could also switch it off by using the flag `-DBUILD_TESTS=OFF` if you just want to build the examples themselves without testing.

```bash
cd CFDGinkgo
mkdir build
cd build
cmake .. && make
```

Now let us run a demonstration code. For running this code, we assume you already have the [OpenCV library](https://opencv.org/) installed. And make sure you locate at `CFDGinkgo/build` directory.

```bash
cd tutorials/demo-heat-equation
./demo-heat-equation
```

If the program successfully runs, it will creates a video file using OpenCV and a custom color mapping as described [here](https://ginkgo-project.github.io/ginkgo-generated-documentation/doc/develop/heat_equation.html).

## Testing

If you have compiled the repository with `-DBUILD_TESTS=ON`, you can run the tests using `make test`. 


