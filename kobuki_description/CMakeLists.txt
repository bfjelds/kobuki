cmake_minimum_required(VERSION 3.5)
project(kobuki_description)
find_package(ament_cmake REQUIRED)
find_package(urdf REQUIRED)
find_package(xacro REQUIRED)

install(DIRECTORY launch
        DESTINATION share
)
install(DIRECTORY meshes
        DESTINATION share
)
install(DIRECTORY rviz
        DESTINATION share
)
install(DIRECTORY urdf
        DESTINATION share
)
