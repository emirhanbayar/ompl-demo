cmake_minimum_required(VERSION 2.80)
project(ompl_tutorials)

find_library(ompl REQUIRED)
find_package(Eigen3 REQUIRED)

macro(add_ompl_demo demo_name)
    add_executable(${ARGV})
    target_link_libraries(${demo_name}
        ompl
        Eigen3::Eigen
        ${Boost_FILESYSTEM_LIBRARY}
        ${Boost_SYSTEM_LIBRARY}
        ${Boost_PROGRAM_OPTIONS_LIBRARY})
endmacro(add_ompl_demo)


add_executable(demo_RigidBodyPlanning RigidBodyPlanning.cpp)
target_link_libraries(demo_RigidBodyPlanning
    ompl
    Eigen3::Eigen
    ${Boost_FILESYSTEM_LIBRARY}
    ${Boost_SYSTEM_LIBRARY}
    ${Boost_PROGRAM_OPTIONS_LIBRARY})