This project is done on Ubuntu 22.04 LTS. To avoid any compatability issues, please adhere to this version of Ubuntu. 

Below are the steps to installing ROS 2 Humble, which is the ROS distribution used for this project. 
For most recent updates on installation commands please use [this link](https://docs.ros.org/en/humble/Installation/Alternatives/Ubuntu-Development-Setup.html)

Updated Command lines (October 23rd, 2024): 

```bash
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```
