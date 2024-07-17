# ROS1 and ROS2 Installation on Ubuntu 20.04

## Prerequisites

- Ubuntu 20.04
- Internet connection

## Step-by-Step Instructions

### 1. Install Git

```bash
sudo apt update
sudo apt install git

### Verify the installation:

```bash
git --version

### 2. Configure Git

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
3. Install ROS1 (Noetic)
### 3.1 Setup your sources.list

``` bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

###3.2 Set up your keys
```bash
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -


###3.3 Update your package index
```bash
sudo apt update
### 3.4 Install ROS Noetic
```bash
sudo apt install ros-noetic-desktop-full
### 3.5 Initialize rosdep
```bash
sudo rosdep init
rosdep update
###3.6 Environment setup
```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
###3.7 Install additional ROS tools
```bash
sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
### 4. Install ROS2 (Foxy)
 - 4.1 Set locale
```bash
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
- 4.2 Setup your sources.list
```bash
sudo apt update && sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo sh -c 'echo "deb http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
 - 4.3 Update your package index
```bash
sudo apt update
 -4.4 Install ROS 2 Foxy
```bash
sudo apt install ros-foxy-desktop
- 4.5 Environment setup
```bash
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
source ~/.bashrc
-4.6 Install additional ROS 2 tools
```bash
sudo apt install python3-argcomplete
###5. Switching between ROS1 and ROS2

- Add these aliases to your ~/.bashrc for easy switching:

```bash
echo "alias ros1='source /opt/ros/noetic/setup.bash'" >> ~/.bashrc
echo "alias ros2='source /opt/ros/foxy/setup.bash'" >> ~/.bashrc
source ~/.bashrc
##Verification
###Verify the installations by running the following commands:

-ROS1:

```bash
roscore
-ROS2:

```bash

ros2 run demo_nodes_cpp talker
