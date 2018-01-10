cmake_minimum_required(VERSION 3.5)
project(kobuki_node)

find_package(ament_cmake REQUIRED)
find_package(rclpy REQUIRED)
find_package(rclcpp REQUIRED)
find_package(pluginlib REQUIRED)
find_package(tf2 REQUIRED)
find_package(angles REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(diagnostic_updater REQUIRED)
find_package(diagnostic_msgs REQUIRED)
find_package(kobuki_msgs REQUIRED)
find_package(kobuki_driver REQUIRED)
find_package(kobuki_keyop REQUIRED)
find_package(kobuki_safety_controller REQUIRED)
find_package(ecl_exceptions REQUIRED)
find_package(ecl_sigslots REQUIRED)
find_package(ecl_streams REQUIRED)
find_package(ecl_threads REQUIRED)

include_directories(include 
  ${rclpy_INCLUDE_DIRS}
  ${rclcpp_INCLUDE_DIRS}
  ${pluginlib_INCLUDE_DIRS}
  ${tf2_INCLUDE_DIRS}
  ${angles_INCLUDE_DIRS}
  ${geometry_msgs_INCLUDE_DIRS}
  ${sensor_msgs_INCLUDE_DIRS}
  ${nav_msgs_INCLUDE_DIRS}
  ${std_msgs_INCLUDE_DIRS}
  ${diagnostic_updater_INCLUDE_DIRS}
  ${diagnostic_msgs_INCLUDE_DIRS}
  ${kobuki_msgs_INCLUDE_DIRS}
  ${kobuki_driver_INCLUDE_DIRS}
  ${kobuki_keyop_INCLUDE_DIRS}
  ${kobuki_safety_controller_INCLUDE_DIRS}
  ${ecl_exceptions_INCLUDE_DIRS}
  ${ecl_sigslots_INCLUDE_DIRS}
  ${ecl_streams_INCLUDE_DIRS}
  ${ecl_threads_INCLUDE_DIRS}
  )

add_subdirectory(src)

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
install(DIRECTORY image
        DESTINATION share
)
install(PROGRAMS scripts/getOdom2D.py
                 scripts/getYaw.py
        DESTINATION bin
)
