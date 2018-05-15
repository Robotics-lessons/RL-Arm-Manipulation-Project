
# Udacity Term 2 Deep Reinforcement Learning Arm Manipulation Project

### Abstract

This project needs to use Deep Reinforcement Learning technology to train an Robotic Arm Manipulation.
The goal is to create a DQN agent and define reward functions to teach a robotic arm to carry out two primary objectives:
    1. Have any part of the robot arm touch the object of interest, with at least a 90% accuracy.
    2. Have only the gripper base of the robot arm touch the object, with at least a 80% accuracy.
 For both objectives, the results were presented in this article.

### Introduction 

Classification includes a broad range of decision-theoretic approaches to the identification of images (or parts thereof). All classification algorithms are based on the assumption that the image in question depicts one or more features (*e.g.*, geometric parts in the case of a manufacturing classification system, or spectral regions in the case of remote sensing) and that each of these features belongs to one of several distinct and exclusive classes. The classes may be specified *a priori* by an analyst (as in *supervised classification*) or automatically clustered (*i.e.* as in *unsupervised classification*) into sets of prototype classes, where the analyst merely specifies the number of desired categories[1].

In this project used a Gazebo environment to build a 3D Robotic Arm Manipulator model and used C++ language to develop the plugin code.


1. P1 moving belt image classification part used P1 dataset pictures of candy boxes, bottles, and nothing (empty conveyor belt).
2. Dog image classification part used the dog image dataset (dog A, dog B and nothing) which Author collected  from iPhone.


### Background / Formulation

​         The P1 image dataset is stored in /data/P1/ directory. It include all images of bottles, candy wrappers and no object on a conveyor belt passing under a camera. A swing arm is used to sort all right objects to correct the bins depending on classifying results. 

P1 dataset image example:


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

Both epoch were set to 5. All other parameters used as default.

#### Results

Evaluating result for AlexNet Model  as:

<img src="C:/projects/Deep_Learning/Udacity/Robotics/Term2/Robotic%20Inference%20project/images/Evaluate_P1_AlexNet.PNG" width="70%" height="60%" title="AlexNet P1 Model">

Evaluating result for GoogLeNet Model  as:

<img src="C:/projects/Deep_Learning/Udacity/Robotics/Term2/Robotic%20Inference%20project/images/P1-Evaluate-GoogleNet-2.PNG" width="70%" height="60%" title="GoogLeNet P1 Model">

Both AlexNet and GoogLeNet models are at least 75 percent accuracy and an inference time of less than 10 ms.

|                        |    AlexNet     |   GoogLeNet    |
| :--------------------: | :------------: | :------------: |
|        Accuacy         | 75.4090360656% | 75.4090360656% |
| Average inference Time |  4.254004 ms   |   5.34768 ms   |

### 2. Dog image classification

#### Background / Formulation

The dog image files located in Output folder, it includes three subfolders, Gany for dog A, Raise for dog B, Nothing for no object.

Dog image example:

<img src="images/val_sample_image.png" width="90%" height="70%" title="Dog image example">

Dog image dataset was split three training, validation and test parts, the color image size is 256 X 256

<img src="images/dog_image_dbcreated-1.png" width="100%" height="70%" title="Dog datasetl">

<video width="320" height="240" controls>
  <source src="images/RL-Manipulator-Arm_worked-2018-05-14_21.48.04.mkv" type="video/mp4">
</video>


#### Data Acquisition:

The dog images were taken from iPhone, then used Augmentation[3] code to generate 500 to 1000 additional images depend the object type.

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

#### Model creation:

GoogLeNet Model was created as : (Use default GoogLeNet network, no change in model itself)

<img src="images/GoogLeNet_dog_epoch50_model.png" width="100%" height="70%" title="GoogLeNet Dog Model">

##### The parameter setting:

Both epoch were set to 50 and Batch size = 50. All other parameters used as default.

####  Results: 

AlexNet and GoogLeNet models, both were built and tested. Compare both of them, the GoogLeNet model has better results. This article only shows GoogLeNet model result.

<img src="images/Digits_main_page.png" width="100%" height="70%" title="Digit Dog Model menu">

This is GoogLeNet model results (epoch = 50, batch size = 50): The result is very good, the accuracy for  all three classes are 100%.

Note:  The number in table is the number of image:

|              | Dog A (Gany) | Dog B (Raise) | No object (Nothing) | Per-class accuracy |
| :----------- | :----------: | :-----------: | :-----------------: | :----------------: |
| Dog A (Gany) |      11      |       0       |          0          |        100%        |
| Dog B (Raise) |      0      |       11       |          0          |        100%        |
| No object (Nothing) |      0      |       0       |          6          |        100%        |

Digits test results screen copy:

<img src="images/GoogLeNet_Dog_epoch50_test_results.png" width="100%" height="70%" title="GoogLeNet Dog Model results">

### Discussion

The original images are almost covering full dog body, using augment code can easily generate different angle and different part of dog body images. There is no problem to use rotate, flip and resize functions to generate new images, but crop image function can cause some image problems if the new image didn't include the target object at all. The image source quality is very important for Deep Learning training result, the manually checking was applying all these generated images to make sure no any nothing image mixed in dog image classes. 

To achieve the best result, the LeNet network was not used because only  28x28 image size and gray color can be used. But AlexNet and GoogLeNet, both networks support 256x256 color image.

Both AlexNet and GoogLeNet have been tested for classification of dog image,  GoogLeNet showed better accuracy than AlexNet at epoch = 20.  According to the research paper from Siddharth Das[4], GoogLeNet had a better performance than AlexNet.

CNNs Architectures:LeNet, AlexNet, VGG, GoogLeNet, ResNet comparing table:

<img src="images/CNN-Architecture_compare.png" width="70%" height="60%" title="CNN architecture comparing">

So GoogLeNet was selected to continue training and testing. Set epoch at 5, 20, 30 and 50 to train the GoogLeNet network, the best result is at epoch = 50, Batch size = 50.

Changed batch size to 50, can reduce training time and use less memory.

### Conclusion 

#### P1 moving belt image classification

Both AlexNet and GoogLeNet models were used with P1 dataset provided by the lesson in moving belt image classification, the results achieved the requirement of Udacity lesson (least 75 percent accuracy and an inference time of less than 10 ms.) 

#### Dog image classification

Using augmentation is a good and fast way  to generate a large number of image from a small set of original images.

Both AlexNet and GoogLeNet models were tested, the GoogLeNet model was better results at same epoch number = 20. 

The same GoogLeNet model, different epoch number 5, 20, 30 and 50 were tested.

The GoogLeNet model (with epoch = 50, Batch size = 50 and test dataset = 1% of total images) achieved the goal (All three classes accuracy are 100%).  

### Future Work

1. Install Nvidia DIGITS system on local PC instead of using cloud GPU resource, the way is no time limitation to implement and test different projects and models.
2.  Include testing object detection and segmentation implementation, and deploying the model on Jetson TX2 board and testing them in real world environment.

### References

[1] S. Perkins, A. Walker and E. Wolfart, Classification "https://homepages.inf.ed.ac.uk/rbf/HIPR2/classify.htm" 2003

[2] Nvidia, DIGITS workflow "https://developer.nvidia.com/digits" 2018

[3] Marcus D. Bloice, Augmentor "https://github.com/mdbloice/Augmentor" 2018

[4] Siddharth Das, CNNs Architectures:LeNet, AlexNet, VGG, GoogLeNet, ResNet and more …  "https://medium.com/@siddharthdas_32104/cnns-architectures-lenet-alexnet-vgg-googlenet-resnet-and-more-666091488df5" 2017