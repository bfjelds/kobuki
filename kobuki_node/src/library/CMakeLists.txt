##############################################################################
# SOURCES
##############################################################################

file(GLOB SOURCES RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)

##############################################################################
# LIBRARY
##############################################################################

add_library(kobuki_ros ${SOURCES})
add_dependencies(kobuki_ros 
  ${rclpy_EXPORTED_TARGETS}
  ${rclcpp_EXPORTED_TARGETS}
  ${pluginlib_EXPORTED_TARGETS}
  ${tf2_EXPORTED_TARGETS}
  ${angles_EXPORTED_TARGETS}
  ${geometry_msgs_EXPORTED_TARGETS}
  ${sensor_msgs_EXPORTED_TARGETS}
  ${nav_msgs_EXPORTED_TARGETS}
  ${std_msgs_EXPORTED_TARGETS}
  ${diagnostic_updater_EXPORTED_TARGETS}
  ${diagnostic_msgs_EXPORTED_TARGETS}
  ${kobuki_msgs_EXPORTED_TARGETS}
  ${kobuki_driver_EXPORTED_TARGETS}
  ${kobuki_keyop_EXPORTED_TARGETS}
  ${kobuki_safety_controller_EXPORTED_TARGETS}
  ${ecl_exceptions_EXPORTED_TARGETS}
  ${ecl_sigslots_EXPORTED_TARGETS}
  ${ecl_streams_EXPORTED_TARGETS}
  ${ecl_threads_EXPORTED_TARGETS}
  )
target_link_libraries(kobuki_ros 
  ${rclpy_LIBRARIES}
  ${rclcpp_LIBRARIES}
  ${pluginlib_LIBRARIES}
  ${tf2_LIBRARIES}
  ${angles_LIBRARIES}
  ${geometry_msgs_LIBRARIES}
  ${sensor_msgs_LIBRARIES}
  ${nav_msgs_LIBRARIES}
  ${std_msgs_LIBRARIES}
  ${diagnostic_updater_LIBRARIES}
  ${diagnostic_msgs_LIBRARIES}
  ${kobuki_msgs_LIBRARIES}
  ${kobuki_driver_LIBRARIES}
  ${kobuki_keyop_LIBRARIES}
  ${kobuki_safety_controller_LIBRARIES}
  ${ecl_exceptions_LIBRARIES}
  ${ecl_sigslots_LIBRARIES}
  ${ecl_streams_LIBRARIES}
  ${ecl_threads_LIBRARIES}
)

install(TARGETS kobuki_ros
        DESTINATION lib
)
