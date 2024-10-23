For most recent updates on command lines to use and updated packages use [this link](https://staging.gazebosim.org/docs/fortress/install_ubuntu)

1. First install some necessary tools:

```bash
sudo apt-get update
sudo apt-get install lsb-release wget gnupg
```

2. Then install Ignition Fortress:

```bash
sudo wget https://packages.osrfoundation.org/gazebo.gpg -O /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt-get update
sudo apt-get install ignition-fortress
```


If you need to uninstall Ignition or switch to a source-based install once you have already installed the library from binaries, run the following command:

```bash
sudo apt remove ignition-fortress && sudo apt autoremove
```
