# Find all .cpp files in the current directory
file(GLOB PROGRAM_SOURCE "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

# Extract the base name of the source file(s) without the extension
get_filename_component(PROGRAM_NAME ${PROGRAM_SOURCE} NAME_WE)

# Add the executable for the program
add_executable(${PROGRAM_NAME} ${PROGRAM_SOURCE})
target_link_libraries(${PROGRAM_NAME} Ginkgo::ginkgo)

# Add tests if test/ folder exist
if(BUILD_TESTS AND EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/test)
    add_tests_for_subdirectory(${PROGRAM_NAME})
endif()

