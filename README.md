# YOLO V4 for darknet_ros
darknet_ros上でYOLO V4を動かせるようにしたリポジトリです。

# Instalution
このリポジトリを導入する環境ではすでに[ROS(Robot Operating System)](https://www.ros.org/)が導入されていることとします。ROSの導入方法は[ros.org](https://www.ros.org/install/)を参考にしてください。私の[構築環境](#Enviroment)はこちらです。


## Create workspace
まずROSのワークスペースを生成します。`<workspace>`は任意の名前をつけてください。
>$ mkdir -p workspace/src
>$ cd workspace/src


## Instalution your enviroment
### Easy Instalution
`darknet`と`darknet_ros`をsubmoduleとして扱うためには、`--recursive`をつけてcloneしてください。
これによりsubmoduleである2つのリポジトリをまとめてcloneすることができます。
> git clone --recursive https://github.com/Tossy0423/yolov4-for-darknet_ros.git

### `darknet`と`darknet_ros`をsubmoduleとして扱わずclone
`darknet`と`darknet_ros`をsubmoduleとして扱わないためには、２つのリポジトリを別々にcloneする必要があります。
>$ git clone https://github.com/Tossy0423/darknet.git
>$ git clone https://github.com/Tossy0423/darknet_ros.git

## make pkg
> $ cd workspace
> $ catkin_make

> echo "source ~/workspace/devel/setup.bash" >> ~/.bashrc



# Enviroment
構築は全てDocker上で行いました。Docker上でなくても動作することは確認しています。

|     Topics     |                     Spec                     |
|:--------------:|:--------------------------------------------:|
|      Model     |              Dell ALIENWARE m15              |
|       CPU      |   Intel® Core™ i7-8750H CPU @ 2.20GHz × 12   |
|       GPU      | GeForce RTX 2070 with Max-Q Design/PCIe/SSE2 |
|       RAM      |                    15.4 GB                   |
|       OS       |           Ubuntu 18.04.3 LTS bionic          |
| Docker version |     Docker version 18.09.3, build 774a1f4    |
|   Midlleware   |                  ROS Melodic                 |  







# How to build this enviroment??
この環境を構築するための手順を示したドキュメントをここに示します。


# Acknowledgment
このリポジトリを構成する大きなリポジトリは、[AlexeyAB](https://github.com/AlexeyAB)の[darknet](https://github.com/AlexeyAB/darknet)、[leggedrobotics](https://github.com/leggedrobotics)の[darknet_ros](https://github.com/leggedrobotics/darknet_ros)で構成されています。
またこの環境の構築には多くの開発者が公開してくれた情報を参考にしました。
これらの素晴らしいリポジトリを公開してくださった開発者、情報提供してくださった多くの開発者に感謝します。


# LISENCE
このリポジトリはMIT Licenseを元にリリースしています。詳しくは`LICENSE`ファイルをご覧ください。
This software is released under the MIT License, see LICENSE.

# Autor
Tossy0423
Please Follow [me](https://twitter.com/gtr35nismo0423)!!
