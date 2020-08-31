<!--
[![people](readmemedia/people.png)](https://www.pexels.com/photo/woman-falling-in-line-holding-each-other-1206059/ "people")\
[![birds](readmemedia/birds.png)](https://www.pexels.com/photo/flock-of-white-and-black-birds-on-ground-4023267/ "birds")\
-->

<div align = "center">
<img src="readmemedia/birds.png" width=70%>
<img src="readmemedia/people.png" width=70%>
</div>

# YOLO V4 for darknet_ros
Thanks for taking a look at this repository!! <br>
This repository is the environment of YOLO V4 ported to darknet_ros. <br>
If you need the Japanese README file, please go [here](./documents/README_ja.md).



# Installation
This repository assumes that the [Robot Operating System (ROS)](https://www.ros.org/) has already been installed on your environment.
See [ros.org](https://www.ros.org/install/) to know how to install ROS. My environment is [here](#Enviroment).

<!-- このリポジトリを導入する環境では, すでに[ROS(Robot Operating System)](https://www.ros.org/)が導入されていることとします. ROSの導入方法は[ros.org](https://www.ros.org/install/)を参考にしてください. 私の[構築環境](#Environment)はこちらです. -->


## Create workspace
First, create the ROS workspace. The `<workspace>` can be named arbitrarily.
<!-- まずROSのワークスペースを生成します. `<workspace>`は任意の名前をつけてください. -->
```bash
## Create workspace for ROS, Change directory
$ mkdir -p workspace/src && cd workspace/src

## init workspace
$ catkin_init_workspace

## Make
$ cd ../
$ catkin_make
```

## Installation your environment
### Easy Installation
To clone `darknet` and `darknet_ros` as a submodule, you must clone them with `--recursive`. This allows you to clone the two submodules together.
<!-- `darknet`と`darknet_ros`をsubmoduleとして扱うためには, `--recursive`をつけて　cloneしてください.
これによりsubmoduleである2つのリポジトリをまとめてcloneすることができます. -->
```bash
$ cd src
$ git clone --recursive https://github.com/Tossy0423/yolov4-for-darknet_ros.git
```


<!-- ### If you don't use `darknet` and `darknet_ros` as a submodule
### `darknet`と`darknet_ros`をsubmoduleとして扱わずclone
To avoid using `darknet` and `darknet_ros` as submodules, you need to clone the two repositories separately.
`darknet`と`darknet_ros`をsubmoduleとして扱わないためには, ２つのリポジトリを別々にcloneする必要があります.
```bash
$ git clone https://github.com/Tossy0423/darknet.git
$ git clone https://github.com/Tossy0423/darknet_ros.git
```
In this case, the tree structure of the folder looks like this.
このやり方の場合, フォルダのツリー構造は以下のようになります.
```
src
├── darknet
│
├── darknet_ros
``` -->

## Download weights file
The weights file is very large and needs to be downloaded separately.
<!-- weightsはファイルサイズが大きので別でダウンロードする必要があります. -->
Download the weights file to `darknet_ros/darknet_ros/yolo_network_config/weights` to install it.
<!-- weightsファイルを導入する場所は, `darknet_ros/darknet_ros/yolo_network_config/weights`へダウンロードしてください. -->
```bash
$ wget https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.weights
```


## make pkg
```bash
# Change workspace directory
$ cd workspace

## Make
$ catkin_make

# Write source command in ~/.bashrc
$ echo "source ~/workspace/devel/setup.bash" >> ~/.bashrc
```


# Environment

|         Topics         	|                     Spec                     	|
|:----------------------:	|:--------------------------------------------:	|
|          Model         	|              Dell ALIENWARE m15              	|
|           CPU          	|   Intel® Core™ i7-8750H CPU @ 2.20GHz × 12   	|
|           GPU          	| GeForce RTX 2070 with Max-Q Design/PCIe/SSE2 	|
|           RAM          	|                    15.4 GB                   	|
|           OS           	|           Ubuntu 18.04.3 LTS bionic          	|
|       Midlleware       	|                  ROS Melodic                 	|
|       NVIDIA-SMI       	|                    440.100                   	|
|     Driver Version     	|                    440.100                   	|
|      CUDA Version      	|                     10.2                     	|
| Cuda compilation tools 	|            release 10.1, V10.1.243           	|



# Demo
I will describe how to demonstrate it in an implemented environment. Before you can do the demo, you need to prepare for it.
<!-- ここまで実装した環境でのデモの方法を述べます. デモをする前に準備すべきことがあります. -->

## Preparation
- Web Camera<br>
  You don't need to have it if it's already installed.
  <!-- ノートPCなどのようにすでに搭載されている場合は用意する必要はありません. -->
  At the Terminal
  <!-- Terminalで -->
  > $ ls /dev/video*

  If you enter and display, you are ready to go.　If you do not see anything, prepare your environment.
  <!-- 入力し表示があれば準備できています.　何も表示されなければ環境を整えてください. -->

- ROS package of `uvc_camera`<br>
    If it has already been installed, there is no need to do it again. To install, execute the following command
  <!-- すでにインストールされている場合は再度行う必要はありません.
  インストールには, 以下のコマンドを実行してください -->
  ```bash
  $ sudo apt install ros-melodic-uvc-camera
  ```
- Fixing the launch file <br>
  If you use the `uvc_camera` package, you need to change the Topic of the camera image to input to darknet_ros. Open the file `darknet_ros/darknet_ros/config/ros.yaml` and change the file as follows
  <!-- `uvc_camera`パッケージを使う場合, カメラ画像のTopicをdarknet_rosへ入力するために変更する必要があります.  任意のエディタで, `darknet_ros/darknet_ros/config/ros.yaml`を開いて以下のように変更します. -->
  ```
  ## Before
  topic: /camera/rgb/image_raw

  ## After
  topic: /image_raw
  ```
## Running
Execute the three commands in another Terminal.
<!-- 以下の3つのコマンドは別のTerminalで実行してください. -->
```bash
$ roscore
$ rosrun uvc_camera uvc_camera_node
$ roslaunch darknet_ros yolo_v4.launch
```
<div align=center>
<img src="readmemedia/camera.png" width=90%>
</div>


# How to build this environment??
Here is the documentation to set up this environment.
<!-- この環境を構築するための手順を示したドキュメントをここに示します. -->


# Acknowledgment
This repository consists of two large repositories, [AlexeyAB](https://github.com/AlexeyAB)'s [darknet](https://github.com/AlexeyAB/darknet) and [legged robotics](https://github.com/leggedrobotics)'s [darknet_ros](https://github.com/leggedrobotics/darknet_ros).
For building this environment, I have a reference to the information published by many developers.
I would like to thank the developers who made these repositories available to me, and many of them have contributed their information to make this environment possible.
<!-- このリポジトリは, [AlexeyAB](https://github.com/AlexeyAB)の[darknet](https://github.com/AlexeyAB/darknet), [leggedrobotics](https://github.com/leggedrobotics)の[darknet_ros](https://github.com/leggedrobotics/darknet_ros)の大きなリポジトリで構成されています.
またこの環境の構築には, 多くの開発者が公開してくれた情報を参考にしました.
これらの素晴らしいリポジトリを公開してくださった開発者, 情報提供してくださった多くの開発者に感謝します. -->


# LISENCE
<!-- このリポジトリはMIT Licenseを元にリリースしています. 詳しくは`LICENSE`ファイルをご覧ください. -->
This software is released under the MIT License, see LICENSE.

# Future Plans
  I will improve it at my whim.
  <!-- 私の気まぐれで改善していきます. -->
  - [x] Rewrite the readme file in English. :earth_americas:
  - [ ] Getting your environment ready to run in the Docker Container. :whale:

# History
  - I've roughly summarized everything from environment building to manual creation(11. Aug. 2020)
  - Create an English version of the README(20. Aug. 2020)
  - Moved `/root/darknet` to `/root/darknet/darknet/darknet_ros` due to redundant file structure.(31. Aug. 2020)

# Autor
Tossy
Japan, Osaka
Please Follow [me](https://twitter.com/gtr35nismo0423)!!
