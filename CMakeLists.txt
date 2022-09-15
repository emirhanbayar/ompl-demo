cmake_minimum_required(VERSION 2.80)
project(ompl_tutorials)

# Find OMPL and Eigen3
find_library(ompl REQUIRED)
find_package(Eigen3 REQUIRED)

# Set location of binary files used to build main.cpp (it is bin/ now)
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set (CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set (CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

# Set compiler flags. Add -g for debugging.
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")

# Macro for adding executable
macro(add_ompl_executable executable_name)
    add_executable(${ARGV})
    target_link_libraries(${executable_name}
        ompl
        Eigen3::Eigen
        ${Boost_FILESYSTEM_LIBRARY}
        ${Boost_SYSTEM_LIBRARY}
        ${Boost_PROGRAM_OPTIONS_LIBRARY})
endmacro(add_ompl_executable)

# Add executables
add_ompl_executable(main src/main.cpp)