cmake_minimum_required(VERSION 2.8.3)
project(robot_playground)

find_package(catkin REQUIRED COMPONENTS roslaunch)

catkin_package(
  LIBRARIES linorobot
  CATKIN_DEPENDS gmapping map_server move_base amcl jackal_gazebo 
  DEPENDS system_lib
)
