# slam-turtlebot-simulation
This will contain the process of how I ran a simulation of the turtlebot3 using ROS melodic

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

The documentation on running a gazebo simulation for a turtlebot3 is provided here https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/#gazebo-simulation

In order to simulate it on gazebo i need to clone the turtlebot3 simulation package repository and compile it in a catkin workspace

```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
Then i just have to export the variable that decides which robot im using (burger)

```
$ export TURTLEBOT3_MODEL=burger
```

Now i am able to launch any of the prebuilt gazebo simulations for the turtlebot3 robot, I will choose one of the simulations

```
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

And to control the robot using WASD input this in another terminal shell

```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

### before moving

![VirtualBoxVM_0fMsXhus5t](https://user-images.githubusercontent.com/25144777/122816750-ccc5ff00-d2df-11eb-9375-39ea90fc9349.png)

### after moving

![VirtualBoxVM_mTZPDNgoS6](https://user-images.githubusercontent.com/25144777/122816769-d0598600-d2df-11eb-87ac-e955faa7a98b.png)

## SLAM simulation

The documentation on running a SLAM simulation for a turtlebot3 is provided here https://emanual.robotis.com/docs/en/platform/turtlebot3/slam_simulation/

I'll start by launching the same simulation world

```
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

Then I'll run a SLAM node using gmapping to start mapping the robot's surrounding obstacles

```
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

And finally, run the process needed to control the robot

```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

### before moving

![VirtualBoxVM_7lAt2ezZho](https://user-images.githubusercontent.com/25144777/122822409-b2435400-d2e6-11eb-99c0-352f43b50cf9.png)

### after moving

![VirtualBoxVM_zEKb5h1DlQ](https://user-images.githubusercontent.com/25144777/122822413-b53e4480-d2e6-11eb-9961-d0a127bd71ae.png)

after revealing the whole map on the RViz SLAM simulation save the map by running

```
$ rosrun map_server map_saver -f ~/map
```

