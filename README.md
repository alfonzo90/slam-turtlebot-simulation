# slam-turtlebot-simulation
This will contain the process of how I ran a simulation of the turtlebot3 on ROS melodic

I'm using the environment I built previously to work on the arduino_robot_arm package, all the documentation can be found in that repository


## installing turtlebot3

Since I already have ROS melodic installed, I started by following the steps documented here https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup

In order to install the turtlebot3 package and all its dependencies I inputted the following

```
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
```

and chose 'burger' as the robot i will work with, so I had to define it in bashrc

```
$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```

Since I'm strictly working on simulations, I decided not to set up the network configuration

## Gazebo simulation

The documentation on running a gazebos imulation for a turtlebot3 are provided here https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/#gazebo-simulation

In order to simulate it on gazebo i need to clone the turtlebot3 simulation package repository and compile it in a catkin workspace

```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```




## SLAM simulation
