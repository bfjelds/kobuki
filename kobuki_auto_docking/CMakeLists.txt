cmake_minimum_required(VERSION 3.5)
project(kobuki_auto_docking)
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclpy REQUIRED)
find_package(pluginlib REQUIRED)
find_package(message_filters REQUIRED)
#find_package(actionlib REQUIRED)
find_package(kdl_conversions REQUIRED)
find_package(ecl_threads REQUIRED)
find_package(ecl_geometry REQUIRED)
find_package(ecl_linear_algebra REQUIRED)
find_package(kobuki_msgs REQUIRED)
find_package(kobuki_dock_drive REQUIRED)

include_directories(include
  ${rclcpp_INCLUDE_DIRS}
  ${rclpy_INCLUDE_DIRS}
  ${pluginlib_INCLUDE_DIRS}
  ${message_filters_INCLUDE_DIRS}
#  ${actionlib_INCLUDE_DIRS}
  ${kdl_conversions_INCLUDE_DIRS}
  ${ecl_threads_INCLUDE_DIRS}
  ${ecl_geometry_INCLUDE_DIRS}
  ${ecl_linear_algebra_INCLUDE_DIRS}
  ${kobuki_msgs_INCLUDE_DIRS}
  ${kobuki_dock_drive_INCLUDE_DIRS}
  )

add_library(kobuki_auto_docking_ros src/auto_docking_ros.cpp)
add_library(kobuki_auto_docking_nodelet src/nodelet.cpp)

add_dependencies(kobuki_auto_docking_ros
  ${rclcpp_EXPORTED_TARGETS}
  ${rclpy_EXPORTED_TARGETS}
  ${pluginlib_EXPORTED_TARGETS}
  ${message_filters_EXPORTED_TARGETS}
#  ${actionlib_EXPORTED_TARGETS}
  ${kdl_conversions_EXPORTED_TARGETS}
  ${ecl_threads_EXPORTED_TARGETS}
  ${ecl_geometry_EXPORTED_TARGETS}
  ${ecl_linear_algebra_EXPORTED_TARGETS}
  ${kobuki_msgs_EXPORTED_TARGETS}
  ${kobuki_dock_drive_EXPORTED_TARGETS}
  )

target_link_libraries(kobuki_auto_docking_ros 
  ${rclcpp_LIBRARIES}
  ${rclpy_LIBRARIES}
  ${pluginlib_LIBRARIES}
  ${message_filters_LIBRARIES}
#  ${actionlib_LIBRARIES}
  ${kdl_conversions_LIBRARIES}
  ${ecl_threads_LIBRARIES}
  ${ecl_geometry_LIBRARIES}
  ${ecl_linear_algebra_LIBRARIES}
  ${kobuki_msgs_LIBRARIES}
  ${kobuki_dock_drive_LIBRARIES}
  )
target_link_libraries(kobuki_auto_docking_nodelet 
  ${rclcpp_LIBRARIES}
  ${rclpy_LIBRARIES}
  ${pluginlib_LIBRARIES}
  ${message_filters_LIBRARIES}
#  ${actionlib_LIBRARIES}
  ${kdl_conversions_LIBRARIES}
  ${ecl_threads_LIBRARIES}
  ${ecl_geometry_LIBRARIES}
  ${ecl_linear_algebra_LIBRARIES}
  ${kobuki_msgs_LIBRARIES}
  ${kobuki_dock_drive_LIBRARIES}
  kobuki_auto_docking_ros)

install(TARGETS kobuki_auto_docking_ros kobuki_auto_docking_nodelet
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
install(DIRECTORY param
        DESTINATION share
)
install(PROGRAMS scripts/DockDriveActionClient.py
                 scripts/DockDriveControl.py
                 scripts/getDockIR.py
        DESTINATION bin
)
