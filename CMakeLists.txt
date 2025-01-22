cmake_minimum_required(VERSION 3.8)
project(alterego_msgs)

# Trova le dipendenze
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(rclpy REQUIRED)

# Definizione dei file di messaggi e servizi
set(msg_files
  "msg/EgoArms.msg"
  "msg/DebugLQR.msg"
  "msg/UpperBodyState.msg"
  "msg/LowerBodyState.msg"
)

set(srv_files
  "srv/NavService.srv"
  "srv/EnableAutoModeService.srv"
  "srv/WhereRUService.srv"
  "srv/LaunchGStreamer.srv"
  "srv/CloseGStreamer.srv"
  "srv/WaitPilotService.srv"
  "srv/HappyPoseService.srv"
  "srv/PickService.srv"
)

# Generazione delle interfacce
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES std_msgs sensor_msgs
)

# Configura il pacchetto
ament_package()
