cmake_minimum_required(VERSION 3.5)
project(kobuki_bumper2pc)
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(pluginlib REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(kobuki_msgs REQUIRED)

include_directories(include 
  ${rclcpp_INCLUDE_DIRS}
  ${pluginlib_INCLUDE_DIRS}
  ${sensor_msgs_INCLUDE_DIRS}
  ${kobuki_msgs_INCLUDE_DIRS}
  )

add_library(kobuki_bumper2pc_nodelet src/kobuki_bumper2pc.cpp)
add_dependencies(kobuki_bumper2pc_nodelet
  ${rclcpp_EXPORTED_TARGETS}
  ${pluginlib_EXPORTED_TARGETS}
  ${sensor_msgs_EXPORTED_TARGETS}
  ${kobuki_msgs_EXPORTED_TARGETS}
  )
target_link_libraries(kobuki_bumper2pc_nodelet
  ${rclcpp_LIBRARIES}
  ${pluginlib_LIBRARIES}
  ${sensor_msgs_LIBRARIES}
  ${kobuki_msgs_LIBRARIES}
  )

install(TARGETS kobuki_bumper2pc_nodelet
        DESTINATION lib
)
install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION include
)
install(DIRECTORY plugins
        DESTINATION share
)
install(DIRECTORY launch
        DESTINATION share
)
