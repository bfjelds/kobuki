cmake_minimum_required(VERSION 3.5)
project(kobuki_testsuite)
find_package(ament_cmake REQUIRED)
find_package(kobuki_driver REQUIRED)
find_package(kobuki_node REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(message_generation REQUIRED)

catkin_python_setup()
catkin_package()

install(PROGRAMS scripts/inf_rotation.py
                 scripts/test_analog_input.py
                 scripts/test_battery_voltage.py
                 scripts/test_events.py
                 scripts/test_gyro.py
                 scripts/test_led_array.py
                 scripts/test_rotation.py
                 scripts/test_sounds.py
                 scripts/scan_angle.py
                 scripts/test_battery
                 scripts/test_digital_output.py
                 scripts/test_external_power.py
                 scripts/test_input.py
                 scripts/test_output.py
                 scripts/test_safewandering.py
                 scripts/test_translation.py
        DESTINATION bin
)
