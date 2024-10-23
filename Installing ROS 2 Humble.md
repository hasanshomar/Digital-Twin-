This project is done on Ubuntu 22.04 LTS. To avoid any compatability issues, please adhere to this version of Ubuntu. 

Below are the steps to installing ROS 2 Humble, which is the ROS distribution used for this project. 
For most recent updates on installation commands please use [this link](https://docs.ros.org/en/humble/Installation/Alternatives/Ubuntu-Development-Setup.html)

Updated Command lines (October 23rd, 2024):

1. Set locale

```bash
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

2. Add the ROS 2 apt repository

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
3. Install development tools and ROS tools

```bash
sudo apt update && sudo apt install -y \
  python3-flake8-docstrings \
  python3-pip \
  python3-pytest-cov \
  ros-dev-tools
```

```bash
sudo apt install -y \
   python3-flake8-blind-except \
   python3-flake8-builtins \
   python3-flake8-class-newline \
   python3-flake8-comprehensions \
   python3-flake8-deprecated \
   python3-flake8-import-order \
   python3-flake8-quotes \
   python3-pytest-repeat \
   python3-pytest-rerunfailures
```

4. Get ROS 2 code

```bash
mkdir -p ~/ros2_humble/src
cd ~/ros2_humble
vcs import --input https://raw.githubusercontent.com/ros2/ros2/humble/ros2.repos src
```

5. Install dependencies using rosdep

```bash
sudo apt upgrade
```

```bash
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src -y --skip-keys "fastcdr rti-connext-dds-6.0.1 urdfdom_headers"
```

6. Build the code in the workspace

```bash
cd ~/ros2_humble/
colcon build --symlink-install
```

7. Source the setup script

```bash
# Replace ".bash" with your shell if you're not using bash
# Possible values are: setup.bash, setup.sh, setup.zsh
. ~/ros2_humble/install/local_setup.bash
```

8. *Try some examples

```bash
. ~/ros2_humble/install/local_setup.bash
ros2 run demo_nodes_cpp talker
```

in a new Terminal tab:

```bash
. ~/ros2_humble/install/local_setup.bash
ros2 run demo_nodes_py listener
```




