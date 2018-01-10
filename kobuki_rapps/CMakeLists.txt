cmake_minimum_required(VERSION 3.5)

project(kobuki_rapps)

find_package(ament_cmake REQUIRED)

install(DIRECTORY rapps DESTINATION share)
