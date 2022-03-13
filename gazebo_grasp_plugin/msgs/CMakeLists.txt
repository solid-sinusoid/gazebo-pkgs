find_package(Protobuf REQUIRED)

set(msgs
 grasp_event.proto
)
PROTOBUF_GENERATE_CPP(PROTO_SRCS PROTO_HDRS ${msgs})
add_library(gazebo_grasp_msgs SHARED ${PROTO_SRCS})
target_link_libraries(gazebo_grasp_msgs ${PROTOBUF_LIBRARY})

## Mark executables and/or libraries for installation
# install(TARGETS gazebo_grasp_msgs
#    ARCHIVE DESTINATION lib
#    LIBRARY DESTINATION lib
#    RUNTIME DESTINATION lib/${PROJECT_NAME}
# )

# install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR} 
#   DESTINATION lib/${PROJECT_NAME}
#   FILES_MATCHING PATTERN "*.pb.h"
# )
