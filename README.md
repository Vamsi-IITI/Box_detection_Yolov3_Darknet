# Box_detection_Yolov3_Darknet
Yolo v3 Darknet for box detection in gazebo. This package provides dataset and training notebooks. As well as trained weights

Reference : [Here](https://annacsmedeiros.medium.com/from-yolo-annotation-to-using-the-weights-with-darknet-ros-2ac0f707dcdb)

> Note : For unknown reasons , yolo v3 tiny weights don't show any predictions when used with darknet ( AlexeyAB ) but Yolo v3 weights work fine.

#### Darknet ROS Installation 
[darknet_ros](https://github.com/leggedrobotics/darknet_ros)
```
cd ~/catkin_ws/src
```
```
git clone --recursive https://github.com/leggedrobotics/darknet_ros.git
```
```
cd ~/catkin_ws
```
```
catkin_make -DCMAKE_BUILD_TYPE=Release
```
## For testing performance of trained weights :


#### Yolo v3 Darknet ( AlexeyAB )
> * Download weights : [Here](https://drive.google.com/file/d/1-JaJxkmwgdYWnXGxo036-e2FO-l3whGm/view?usp=sharing)
> * Download sample test images : [Here](https://drive.google.com/drive/folders/1HZXlCgzpd6g3R5YdNYnkyR-7H3vZwI0P?usp=sharing)
> 
> ```
> cd ~
> git clone https://github.com/AlexeyAB/darknet.git
> cd darknet
> ```
> ( Make sure you have downloaded necessary libraries , please refer to these guides [1](https://robocademy.com/2020/05/01/a-gentle-introduction-to-yolo-v4-for-object-detection-in-ubuntu-20-04/) and [2](https://medium.com/geekculture/yolov4-darknet-installation-and-usage-on-your-system-windows-linux-8dec2cea6e81#a59a) )
>
> Make changes in Makefile and save them using gedit or code (vs code)
> ```
> code Makefile
> ```
> For CPU build , set following parameters in Makefile :
>> ```GPU=0
>> CUDNN=0
>> CUDNN_HALF=0
>> OPENCV=1
>> AVX=1
>> OPENMP=1
>> LIBSO=1  
>> ZED_CAMERA=0
>> ZED_CAMERA_v2_8=0
>> ```
>> Save the edited Makefile
> ```
> make
> ```
> Now copy obj.data , obj.names and yolov3_training.cfg files from ~/Object_follower_UR5/src/yolov3/cfg folder to cfg folder of darknet directory. Also place weights file in darknet directory
> Now place any test image ( for example here it is two_boxes.png ) in darknet directory and run following command :
> ```
> cd ~/darknet
> ./darknet detector test cfg/obj.data cfg/yolov3_training.cfg yolov3_training.weights two_boxes.png
> ```
> Watch the predictions of model! (**Task 3 - Object Detection**)
> 
> ![predictions](https://github.com/Vamsi-IITI/Object_follower_UR5/assets/92263050/5b41d583-c8f7-470b-807a-4629b3b6628e)
