
# Forward and inverse kinematics

Make sure you are using robo-nd VM or have Ubuntu+ROS installed locally.

### One time Gazebo setup step:
Check the version of gazebo installed on your system using a terminal:
```sh
$ gazebo --version
```
To run projects from this repository you need version 7.7.0+
If your gazebo version is not 7.7.0+, perform the update as follows:
```sh
$ sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
$ wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install gazebo7
```

Once again check if the correct version was installed:
```sh
$ gazebo --version
```
### For the rest of this setup, catkin_ws is the name of active ROS Workspace, if your workspace name is different, change the commands accordingly

If you do not have an active ROS workspace, you can create one by:
```sh
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
```

Now that you have a workspace, clone or download this repo into the **src** directory of your workspace:
```sh
$ cd ~/catkin_ws/src
$ git clone https://github.com/Junzhuodu/Forward-Inverse-Kinematics.git
```

Now from a terminal window:

```sh
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src --rosdistro=kinetic -y
```
Build the project:
```sh
$ cd ~/catkin_ws
$ catkin_make
```

Add following to your .bashrc file
```
export GAZEBO_MODEL_PATH=~/catkin_ws/src/Forward-Inverse-Kinematics/kuka_arm/models

source ~/catkin_ws/devel/setup.bash
```

[//]: # (Image References)

[image1]: ./misc_images/misc1.png
[image2]: ./misc_images/misc4.png
[image3]: ./misc_images/misc5.png

### Spend some time playing with KR210 model
```
$ roslaunch kuka_arm forward_kinematics.launch 
```
If successful, you should see:
![alt text][image1]

You can use `tf_echo` command on ROS to easily obtain the transform between parent and child links from the TF display on the left side panel.
```
$ rosrun tf tf_echo [reference frame] [target frame] 
```
![alt text][image2]

Open another terminal window and type:
```
$ rosrun tf tf_echo base_link gripper_link
```
You can use the `tf_echo` command to obtain the orientation and position of the end-effector. 
![alt text][image3]

**As for how to create forward kinematics and inverse kinematics for KR210, you can read the `writeup.md` file.**

### Debugging Forward Kinematics
After you finsh your forward kinematics section, you can run `Calculate_FK.py` to verify that each individual transform is correct.
```
$ python Calculate_FK.py
```

### Debugging Inverse Kinematics
After you finish your inverse kinematics section, you can run `Calculate_IK.py` to check your inverse calculations. 
```
$ python Calculate_IK.py
```

