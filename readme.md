# Simultaneous Localization And Mapping (SLAM)

The SLAM implementation of Real-Time Appearance Based Mapping (RTABMap) is used in this project to map two simulated worlds made in Gazebo.


## Blank Ubuntu 16.04 Project Setup Instructions
This project is implemented on a desktop computer, therefore the following steps must be performed first:

1. Install ROS: 
```shell
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' && sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116 && sudo apt-get update && sudo apt-get install ros-kinetic-desktop-full && sudo rosdep init && rosdep update && echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc && source ~/.bashrc
```

Note: Skip this step if ROS is already installed.

2. Install dependencies: 
```shell
sudo apt-get install ros-kinetic-rtabmap ros-kinetic-rtabmap-ros
```

3. Install RTAB-Map:
```shell 
cd ~ && git clone https://github.com/introlab/rtabmap.git rtabmap && cd rtabmap/build && cmake .. && make && sudo make install
```

4. Create .gazebo folder: Open gazebo and then close it.

5. Add model collision adjustments: 
```shell
curl -L https://s3-us-west-1.amazonaws.com/udacity-robotics/Term+2+Resources/P3+Resources/models.tar.gz | tar zx -C ~/.gazebo/
```


## Getting Started:

First, create a workspace folder under home directory. Initialize the workspace and run catkin_make.

```shell
$ mkdir -p zeng_catkin_ws/src
$ cd zeng_catkin_ws/src
$ catkin_init_workspace
$ cd ..
$ catkin_make
$ source devel/setup.bash
```

Download and unzip the submitted package as `slam_project`, and place the `slam_project` folder under `src` directory.

Then, change directory to `src`, install slam_project, and run catkin_make.

```shell
$ cd zeng_catkin_ws/src
$ rosdep -i install slam_project
$ catkin_make
$ source devel/setup.bash
```

### Launching everything
Note: each step should be ran in a new terminal.

1. **Launch world and robot:**
```shell
$ source devel/setup.bash
$ roslaunch slam_project world.launch map:=kitchen_dining
```
To load the custom map, please change `map:=kitchen_dining` to `map:=custom`

2. **Start the teleop:**
```shell
$ source devel/setup.bash
$ roslaunch slam_project teleop.launch
```

3. **Start the Mapping:**
```shell
$ source devel/setup.bash
$ roslaunch slam_project mapping.launch
```
4. **Rviz:**
```shell
$ source devel/setup.bash
$ roslaunch slam_project rviz.launch
```

## Database
Please download the database for the mapping of kitchen world from the following urls:
https://we.tl/t-fc7eUooQ1P
or
https://wetransfer.com/downloads/dd0371491877f8435d3d9aea8370c73c20190325095019/3fe958

