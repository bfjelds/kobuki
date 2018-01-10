cmake_minimum_required(VERSION 3.5)
project(kobuki_controller_tutorial)
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(pluginlib REQUIRED)
find_package(std_msgs REQUIRED)
find_package(kobuki_msgs REQUIRED)
find_package(yocs_controllers REQUIRED)

include_directories(include
  ${rclcpp_INCLUDE_DIRS}
  ${pluginlib_INCLUDE_DIRS}
  ${std_msgs_INCLUDE_DIRS}
  ${kobuki_msgs_INCLUDE_DIRS}
  ${yocs_controllers_INCLUDE_DIRS}
  )

add_library(bump_blink_controller_nodelet src/nodelet.cpp)
add_dependencies(bump_blink_controller_nodelet 
  ${rclcpp_EXPORTED_TARGETS}
  ${pluginlib_EXPORTED_TARGETS}
  ${std_msgs_EXPORTED_TARGETS}
  ${kobuki_msgs_EXPORTED_TARGETS}
  ${yocs_controllers_EXPORTED_TARGETS}
  )
target_link_libraries(bump_blink_controller_nodelet
  ${rclcpp_LIBRARIES}
  ${pluginlib_LIBRARIES}
  ${std_msgs_LIBRARIES}
  ${kobuki_msgs_LIBRARIES}
  ${yocs_controllers_LIBRARIES}
  )

install(TARGETS bump_blink_controller_nodelet
        DESTINATION lib)
install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION include)
        
install(DIRECTORY plugins
        DESTINATION share)
        
install(DIRECTORY launch
        DESTINATION share)
