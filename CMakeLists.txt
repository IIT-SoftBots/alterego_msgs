cmake_minimum_required(VERSION 3.22)
project(alterego_msgs)

# ROS2 interface package migration from ROS1 (catkin -> ament + rosidl)
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(geometry_msgs REQUIRED) # Needed by MarkerInfo.msg

set(msg_files
  "msg/EgoArms.msg"
  "msg/DebugLQR.msg"
  "msg/UpperBodyState.msg"
  "msg/LowerBodyState.msg"
  "msg/MarkerInfo.msg"
)

set(srv_files
  "srv/NavService.srv"
  "srv/EnableAutoModeService.srv"
  "srv/WhereRUService.srv"
  "srv/LaunchGStreamer.srv"
  "srv/CloseGStreamer.srv"
  "srv/WaitPilotService.srv"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES std_msgs sensor_msgs geometry_msgs
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()