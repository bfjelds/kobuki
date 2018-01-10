cmake_minimum_required(VERSION 3.5)
project(kobuki_keyop)
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(std_srvs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(rclcpp REQUIRED)
find_package(ecl_exceptions REQUIRED)
find_package(ecl_threads REQUIRED)
find_package(ecl_time REQUIRED)
find_package(kobuki_msgs REQUIRED)

include_directories(include 
  ${geometry_msgs_INCLUDE_DIRS}
  ${std_srvs_INCLUDE_DIRS}
  ${std_msgs_INCLUDE_DIRS}
  ${rclcpp_INCLUDE_DIRS}
  ${ecl_exceptions_INCLUDE_DIRS}
  ${ecl_threads_INCLUDE_DIRS}
  ${ecl_time_INCLUDE_DIRS}
  ${kobuki_msgs_INCLUDE_DIRS}
  )

add_subdirectory(src)

install(DIRECTORY include
  DESTINATION include
  FILES_MATCHING PATTERN "*.h*")

install(DIRECTORY launch
        DESTINATION share
)
install(DIRECTORY param
        DESTINATION share
)
