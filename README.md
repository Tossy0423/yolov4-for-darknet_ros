# YOLO V4 for darknet_ros
darknet_ros上でYOLO V4を動かせるようにしたリポジトリです。

# Instalution
## Easy Instalution
`darknet`と`darknet_ros`をsubmoduleとして扱うためには、`--recursive`をつけてcloneしてください。
これによりsubmoduleである2つのリポジトリをまとめてcloneすることができます。
> git clone --recursive https://github.com/Tossy0423/yolov4-for-darknet_ros.git

## `darknet`と`darknet_ros`をsubmoduleとして扱わずclone
`darknet`と`darknet_ros`をsubmoduleとして扱わないためには、２つのリポジトリを別々にcloneする必要があります。
> git clone https://github.com/Tossy0423/darknet.git
> git clone https://github.com/Tossy0423/darknet_ros.git

# Enviroment
動作は全てDocker上で行いました。

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
