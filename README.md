# voice_control
这个是我自己根据科大讯飞的语音流式听写官方示例自己写的一个语音控制ros机器人的功能包

实验平台：RDK X5（理论上适配树莓派等Linux开发板）

麦克风：usb麦克风

由于不同麦克风的采样率不同，而科大讯飞官方要求该采样率必须为16000，且必须为单通道，所以作者在代码中进行了转换，可以适配任何采样率的麦克风只需要在代码中修改

![image](https://github.com/user-attachments/assets/a2890fdb-797c-484a-a2e2-77377f95aefa)

需要修改项目中的voice_control中的voice_control_node.py中的RATE_ORIGINAL，如上图所示。

由于本项目是调用科大讯飞的语音听写API，所以需要获取科大讯飞的相关API参数
![image](https://github.com/user-attachments/assets/655bbb2e-5ff9-45ec-9289-713fa4f4c660)
![image](https://github.com/user-attachments/assets/34f68273-db49-4b42-a782-287ef438c301)
![image](https://github.com/user-attachments/assets/8678852c-5daf-41d0-b54d-ceb91193c133)
将这里的XFYUN_APPID， XFYUN_APIKEY， XFYUN_APISECRET复制下来
在环境变量中进行设置，即将下面三行代码复制进.bashrc文件中
export XFYUN_APPID=xxx
export XFYUN_APIKEY=xxx
export XFYUN_APISECRET=xxx

还要注意自己的usb麦克风的设备编号，根据实际情况修改
![image](https://github.com/user-attachments/assets/dc9f767d-9917-41cc-bbf7-8aa74a407f98)

接下来就是编译功能包，运行功能包

ros2 launch voice_control voice_control.launch.py
对着麦克风说前进、后退、左转、右转即可
