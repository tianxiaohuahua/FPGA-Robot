# FPGA-Robot
使用FPGA制作机器人，并使用python建立上位机，FPGA机器人通过控制ESP8266通过WiFi进行无线通讯，来达到上位机控制FPGA机器人的目的

摄像头为机器人提供实时监控，并把画面传输到显示屏上。网络通讯可以把各个传感器采集的数据传输给 PC 上位机。同时上位机也可以通过 WiFi 无线控制机器人进行一些动作和移动的操作。PC 上位机使用 python 脚本构建了一个TCP 协议的客户端，在机器人上使用 ESP8266 模块连接路由器同时构建为服务器模式。PC 上位机通过 WiFi 连接机器人进行数据的收发。

机器人系统的系统内部的图像部分和其他部分分开设计。由驱动 ESP8266 的模块为核心模块。为了方便操作和拓展，使用 ESP8266 的 AT 指令模式进行操作。使用串口和 8266 模块通讯。其他模块为了配合数据传送，输入输出全部设计成为 ASSIC 码，因此在各个模块之间传输的数据大部分都采用了 ASSIC 码的数据传输。

在没有外部控制信号的时候，机器人进入自动控制管理状态，由自动管理模块 automation 来控制数据处理模块，进而控制机器人完成一定的动作和指令，比如控制舵机的云台转动，自动向上位机发送温湿度，等数据。在上位机有人操作控制机器人的时候，机器人会关闭无人管理模块，通过接收上位机发送过来的数据来控制舵机和电机让机器人实现一系列的操作，比如控制机器人移动以及调整舵机的云台角度。

