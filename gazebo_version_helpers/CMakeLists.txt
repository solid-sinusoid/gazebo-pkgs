cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(gazebo_version_helpers)

find_package(gazebo REQUIRED)

set(INCLUDE_DIR 
    include
    ${GAZEBO_INCLUDE_DIRS}    
)

include_directories(${INCLUDE_DIR})
link_directories(${GAZEBO_LIBRARY_DIRS})
list(APPEND CMAKE_CXX_FLAGS "${GAZEBO_CXX_FLAGS}")

add_library(${PROJECT_NAME} SHARED src/GazeboVersionHelpers.cpp)
target_link_libraries(${PROJECT_NAME} ${GAZEBO_LIBRARIES})

# install(TARGETS ${PROJECT_NAME}
#     LIBRARY DESTINATION lib
#     ARCHIVE DESTINATION lib  
# )

# install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
#     DESTINATION include
# )