##############################################################################
# Sources
##############################################################################

file(GLOB SOURCES RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)

##############################################################################
# Targets
##############################################################################

add_executable(keyop ${SOURCES})
add_dependencies(keyop 
  ${geometry_msgs_EXPORTED_TARGETS}
  ${std_srvs_EXPORTED_TARGETS}
  ${std_msgs_EXPORTED_TARGETS}
  ${rclcpp_EXPORTED_TARGETS}
  ${ecl_exceptions_EXPORTED_TARGETS}
  ${ecl_threads_EXPORTED_TARGETS}
  ${ecl_time_EXPORTED_TARGETS}
  ${kobuki_msgs_EXPORTED_TARGETS}
  )
target_link_libraries(keyop
  ${geometry_msgs_LIBRARIES}
  ${std_srvs_LIBRARIES}
  ${std_msgs_LIBRARIES}
  ${rclcpp_LIBRARIES}
  ${ecl_exceptions_LIBRARIES}
  ${ecl_threads_LIBRARIES}
  ${ecl_time_LIBRARIES}
  ${kobuki_msgs_LIBRARIES}
  )

install(TARGETS keyop
        DESTINATION bin
)
