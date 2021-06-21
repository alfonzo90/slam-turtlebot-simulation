# slam-turtlebot-simulation
This will contain the process of how I ran a simulation of the turtlebot3 on ROS melodic

I'm using the environment I built previously to work on the arduino_robot_arm package, all the documentation can be found in that repository


## installing turtlebot3
Since I already have ROS melodic installed, I started by following the steps documented here https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup.

In order to install the turtlebot3 package and all its dependencies I inputted the following

```
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
```

and chose 'burger' as the robot i will work with, so I had to define it in the environment

```
$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```

## Gazebo simulation




## SLAM simulation
