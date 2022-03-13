cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(gazebo-pkgs)

add_subdirectory(gazebo_version_helpers)
add_subdirectory(gazebo_grasp_plugin)

#target_link_libraries(gazebo_grasp_plugin gazebo_version_helpers)