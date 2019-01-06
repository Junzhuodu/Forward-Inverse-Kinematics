## How to create forward kinematics and inverse kinematics 

---

**Steps to complete the project:**  

[//]: # (Image References)

[image1]: ./misc_images/misc1.png
[image2]: ./misc_images/misc2.png
[image3]: ./misc_images/misc6.png
[image4]: ./misc_images/misc7.png
[image5]: ./misc_images/misc8.png
[image6]: ./misc_images/misc9.png
[image7]: ./misc_images/misc3.png
[image8]: ./misc_images/misc10.png
[image9]: ./misc_images/misc11.png

### Kinematic Analysis
#### 1. Run the forward_kinematics demo and evaluate the kr210.urdf.xacro file to perform kinematic analysis of Kuka KR210 robot and derive its DH parameters.


![alt text][image1]
![alt text][image2]

You can get the schematic of the KUKA KR210:
![alt text][image3]

Then you can label joints from 1 to n, define joints axes and labes links from 0 to n.
![alt text][image4]

Define common normals and reference frame origins.
![alt text][image5]

Reading `kr210.urdf.xacro` file, you can get parameters as follow:
![alt text][image6]


#### 2. Using the DH parameter table you derived earlier, create individual transformation matrices about each joint. In addition, also generate a generalized homogeneous transform between base_link and gripper_link using only end-effector(gripper) pose.

Links | alpha(i-1) | a(i-1) | d(i-1) | theta(i)
--- | --- | --- | --- | ---
0->1 | 0 | 0 | 0.75 | qi
1->2 | - pi/2 | 0.35 | 0 | -pi/2 + q2
2->3 | 0 | 1.25 | 0 | q3
3->4 |  -pi/2 | -0.054 | 1.5 | q4
4->5 | pi/2 | 0 | 0 | q5
5->6 | -pi/2 | 0 | 0 | q6
6->EE | 0 | 0 | 0.303 | 0

**Note: There are difference between the gripper reference frame as defined in the urdf versus the DH tables. You need to compensate it later.
![alt text][image8]

#### 3. Decouple Inverse Kinematics problem into Inverse Position Kinematics and inverse Orientation Kinematics; doing so derive the equations to calculate all individual joint angles.

And here's where you can draw out and show your math for the derivation of your theta angles. 

![alt text][image7]
![alt text][image9]


