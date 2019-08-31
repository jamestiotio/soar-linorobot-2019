# robot_playground
 [Jackal](https://www.clearpathrobotics.com/jackal-small-unmanned-ground-vehicle/) Simulation running on Linorobot's Navigation Stack parameters.

This package creates a shim to Jackal's Gazebo simulator so you can run a virtual robot on Gazebo and try Linorobot's Navigation Stack parameters.

A forked [version](https://github.com/grassjelly/jackal) of Jackal is used so that the frames and topics on the virtual robot match Linorobot's. You can check out the following commits to see what changes have been made to make Jackal and Linorobot compatible.

- [remapping of Odometry topic 'odometry/filtered' to 'odometry'](https://github.com/grassjelly/jackal/commit/572e1122267e4a6550909229c9dff9a55729a064)
- [remapping of Laser's 'front/scan' topic to 'scan' topic](https://github.com/grassjelly/jackal/commit/edf8c5cf8bd3ab2648ed4a37824995f624ee5ce2)
- [remapping of Laser's 'front_laser' frame to 'laser frame'](https://github.com/grassjelly/jackal/commit/505f6c324f3fcbdd11de7414aac37039dc8d8aa9)
- [remapping of Base's 'base_link' frame to 'base_footprint frame'](https://github.com/grassjelly/jackal/commit/6aaabba108f841097a35dd87aecfaf8b6b8d8be9)
- [defining 'base_footprint' frame as base_frame_id on jackal_velocity_controller](https://github.com/grassjelly/jackal/commit/423cfaa99db4b0cec3e8b72f30d3b9c5a38d8bd9)

## Installation

### Install dependencies:

    ./installdep

### Clone Jackal's and playground's sources on your linorobot_ws:

    cd ~/linorobot_ws/src
    
    git clone https://github.com/grassjelly/jackal.git
    git clone https://github.com/jackal/jackal_simulator.git
    git clone https://github.com/jackal/jackal_desktop.git
    git clone https://github.com/ros-visualization/interactive_marker_twist_server.git
    
    cd ../
    catkin_make
    source devel/setup.bash


Credits to vfdev-5's Jackal [installation](https://gist.github.com/vfdev-5/57a0171d8f5697831dc8d374839bca12).

## Simulation
You can change the sensors used by uncommenting the sensors you need in bringup_sim.launch.

Running the virtual robot and Gazebo World:

    roslaunch robot_playground bringup_sim.launch

Once Jackal's simulation is up, you can run Linorobot's gmapping and autonomous navigation launch files as per normal.

Running gmapping demo:

    roslaunch linorobot slam.launch

Running autonomous navigation:

    roslaunch linorobot navigate.launch


## Navigation Stack Tuning

Some useful resources to tune your parameters:

-  [Kaiyu Zheng's](http://kaiyuzheng.me/documents/navguide.pdf) - very comprehensive guide

- [ROS'](http://wiki.ros.org/navigation/Tutorials/Navigation%20Tuning%20Guide) - high level description of each parameter