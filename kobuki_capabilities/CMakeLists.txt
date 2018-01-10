cmake_minimum_required(VERSION 3.5)

project(kobuki_capabilities)

find_package(ament_cmake REQUIRED)

install(DIRECTORY interfaces DESTINATION share)
install(DIRECTORY providers DESTINATION share)