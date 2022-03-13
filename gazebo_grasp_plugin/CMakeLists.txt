cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(gazebo_grasp_plugin)

find_package(gazebo REQUIRED)
#find_package(gazebo_version_helpers REQUIRED)

set(INCLUDE_DIR
    include
    ${GAZEBO_INCLUDE_DIRS}
    ${CMAKE_CURRENT_BINARY_DIR}
    ${CMAKE_SOURCE_DIR}/gazebo_version_helpers/include
    #gazebo_version_helpers
)
set(LIB_SOURCES
    src/GazeboGraspFix.cpp
    src/GazeboGraspGripper.cpp
)

include_directories(${INCLUDE_DIR})
link_directories(
    ${GAZEBO_LIBRARY_DIRS}
    )
list(APPEND CMAKE_CXX_FLAGS "${GAZEBO_CXX_FLAGS}")

add_subdirectory(msgs)
#target_include_directories(gazebo_grasp_fix PUBLIC ${CMAKE_SOURCE_DIR}/gazebo_version_helpers)
add_library(gazebo_grasp_fix SHARED ${LIB_SOURCES})
#add_dependencies(gazebo_grasp_fix gazebo_graso_msgs gazebo_version_helpers)
target_link_libraries(gazebo_grasp_fix gazebo_grasp_msgs gazebo_version_helpers ${GAZEBO_LIBRARIES} ${Boost_LIBRARIES})

# install(TARGETS gazebo_grasp_fix
#     LIBRARY DESTINATION lib
#     ARCHIVE DESTINATION lib    
# )

# install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
#     DESTINATION include
# )