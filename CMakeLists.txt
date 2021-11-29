cmake_minimum_required(VERSION 3.0.2)
project(localization)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  sensor_msgs
  std_msgs
)

find_package(OpenCV REQUIRED)

set( sources
  src/main.cpp
  src/c_ekf.cpp
  src/CoordinateConv.cpp
)

set( headers
  src/main.h
  src/common_def.h
  src/c_ekf.h
  src/CoordinateConv.h
)

catkin_package(
  LIBRARIES navi
  CATKIN_DEPENDS roscpp sensor_msgs std_msgs 
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_executable(${PROJECT_NAME}_node ${headers} ${sources})

target_link_libraries(${PROJECT_NAME}_node
   ${catkin_LIBRARIES}
   ${OpenCV_LIBRARIES}
)
