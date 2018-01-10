cmake_minimum_required(VERSION 3.5)
project(kobuki_random_walker)
find_package(ament_cmake REQUIRED)
find_package(ecl_threads REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(kobuki_msgs REQUIRED)
find_package(pluginlib REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(yocs_controllers REQUIRED)

include_directories(include
  ${ecl_threads_INCLUDE_DIRS}
  ${geometry_msgs_INCLUDE_DIRS}
  ${kobuki_msgs_INCLUDE_DIRS}
  ${pluginlib_INCLUDE_DIRS}
  ${rclcpp_INCLUDE_DIRS}
  ${std_msgs_INCLUDE_DIRS}
  ${yocs_controllers_INCLUDE_DIRS}
  )

add_library(kobuki_random_walker_nodelet src/nodelet.cpp)
add_dependencies(kobuki_random_walker_nodelet
  ${ecl_threads_EXPORTED_TARGETS}
  ${geometry_msgs_EXPORTED_TARGETS}
  ${kobuki_msgs_EXPORTED_TARGETS}
  ${pluginlib_EXPORTED_TARGETS}
  ${rclcpp_EXPORTED_TARGETS}
  ${std_msgs_EXPORTED_TARGETS}
  ${yocs_controllers_EXPORTED_TARGETS}
  )
target_link_libraries(kobuki_random_walker_nodelet
  ${ecl_threads_LIBRARIES}
  ${geometry_msgs_LIBRARIES}
  ${kobuki_msgs_LIBRARIES}
  ${pluginlib_LIBRARIES}
  ${rclcpp_LIBRARIES}
  ${std_msgs_LIBRARIES}
  ${yocs_controllers_LIBRARIES}
  )

install(TARGETS kobuki_random_walker_nodelet
        DESTINATION lib)
        
install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION include)

install(DIRECTORY param
        DESTINATION share)

install(DIRECTORY plugins
        DESTINATION share)

install(DIRECTORY launch
        DESTINATION share)
