# Find all .cpp files in the current directory
file(GLOB PROGRAM_SOURCE "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

# Extract the base name of the source file(s) without the extension
get_filename_component(PROGRAM_NAME ${PROGRAM_SOURCE} NAME_WE)

# Find OpenCV used for plotting
find_package(OpenCV REQUIRED)

# Add the executable for the program
add_executable(${PROGRAM_NAME} ${PROGRAM_SOURCE})
target_link_libraries(${PROGRAM_NAME} Ginkgo::ginkgo ${OpenCV_LIBS})

# Add tests if test/ folder exist
if(BUILD_TESTS AND EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/test)
    add_tests_for_subdirectory(${PROGRAM_NAME})
endif()

# Copy the data files to the execution directory
configure_file(data/gko_logo_2d.mtx data/gko_logo_2d.mtx COPYONLY)
configure_file(data/gko_text_2d.mtx data/gko_text_2d.mtx COPYONLY)

