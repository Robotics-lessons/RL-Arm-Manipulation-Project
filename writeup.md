
# Udacity Term 2 Deep Reinforcement Learning Arm Manipulation Project

### Abstract

This project needs to use Deep Reinforcement Learning technology to train an Robotic Arm Manipulation.
The goal is to create a DQN agent and define reward functions to teach a robotic arm to carry out two primary objectives:
    1. Have any part of the robot arm touch the object of interest, with at least a 90% accuracy.
    2. Have only the gripper base of the robot arm touch the object, with at least a 80% accuracy.
 For both objectives, the results were presented in this article.

### Introduction 



In this project used a Gazebo environment to build a 3D Robotic Arm Manipulator model and used C++ language to develop the plugin code.




### Background / Formulation

​         


<img src="images/gazebo_arm.jpg" width="70%" height="60%" title="GoogLeNet P1 Model">

<img src="images/nv-rl-stack-diagram.jpg" width="80%" height="80%" title="GoogLeNet P1 Model">

#### Data Acquisition:



<video width="320" height="240" controls>
  <source src="images/RL_Manipulator_Arm.mp4" type="video/mp4">
</video>



```
<script src="http://vjs.zencdn.net/4.0/video.js"></script>

<video id="pelican-installation" class="video-js vjs-default-skin" controls
preload="auto" width="683" height="384" poster="images/gazebo_arm.jpg"
data-setup="{}">
<source src="images/RL_Manipulator_Arm.mp4" type='video/mp4'>
</video>
```


#### Model creation:



<img src="images/project-1-P1-GooglrNet-1.png" width="70%" height="60%" title="GoogLeNet P1 Model">

##### The parameter setting:  



#### Results



|              | Dog A (Dany) | Dog B (Raise) | No object (Nothing) |
| ------------ | :----------: | :-----------: | :-----------------: |
| iPhone images | 193 | 156 | 62 |
| Augment generated images | 887 | 998 | 612 |
| Total images  | 1080 | 1154 | 674 |

The dog database was created as:

|              | Training | Validating | Testing |
| ------------ | :----------: | :-----------: | :-----------------: |
| Image number | 2185 | 695 | 28 |
| Percentage | 75% | 24% | 1% |



####  Results: 



### Discussion

### Conclusion 

### Future Work

1. Install Nvidia DIGITS system on local PC instead of using cloud GPU resource, the way is no time limitation to implement and test different projects and models.
2.  Include testing object detection and segmentation implementation, and deploying the model on Jetson TX2 board and testing them in real world environment.

### References

[1] S. Perkins, A. Walker and E. Wolfart, Classification "https://homepages.inf.ed.ac.uk/rbf/HIPR2/classify.htm" 2003

[2] Nvidia, DIGITS workflow "https://developer.nvidia.com/digits" 2018

[3] Marcus D. Bloice, Augmentor "https://github.com/mdbloice/Augmentor" 2018

[4] Siddharth Das, CNNs Architectures:LeNet, AlexNet, VGG, GoogLeNet, ResNet and more …  "https://medium.com/@siddharthdas_32104/cnns-architectures-lenet-alexnet-vgg-googlenet-resnet-and-more-666091488df5" 2017