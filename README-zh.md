## Tuya webrtc demo


English Version：[English](README.md)


## 功能概述

涂鸦智能webrtc demo提供了Android App通过webrtc连接IPC摄像头的使用示例。
demo展示了app通过webrtc连接ipc摄像头的整个流程，包括：接口、mqtt连接、sdp交互等。

主要包括了以下功能： 

1.获取token、获取mqtt登陆信息和设备相关的webrtc信息等。

2.mqtt登陆、订阅、消息发送和接收等。

3.webrtc sdp交互等。

4.通过app浏览摄像头的视频，并和摄像头进行语音通话。

## 使用步骤

1. 通过iot账号获取clientid：

2. 通过下面到url进行授权，获取到授权码：
    先填充clientid和用户账号，然后在浏览器运行下面的链接进行授权。
    https://openapi-cn.wgine.com/login/open/tuya/login/v1/index.html?client_id=clientid(第1步获取到的clientId）clientid&redirect_uri=https://www.example.com/auth&state=1234&username=（用户账号）&app_schema=tuyasmart&is_dynamic=true
    授权成功后返回如下：
    https://www.example.com/auth?code=xxxxxxxxxxxxxxxxxxxx&state=1234&platform_url=https://openapi-cn.wgine.com
    这个rul里面的code 即是授权码。
    
3. 通过app 或者别的手段 获取到需要访问到摄像头到did和localKey .

4. 修改demo里面的相应参数：
   具体文件名 CallActivity
   clientId_ =        // 第1步获取到到clientid ;
   secret_   =        // 第1不获取到到secret
   authCode_ =        // 第2步获取到到授权码
   deviceId_ =        // 第3步获取到到设备ID
   localKey_ =        // 第3步获取到到设备LoclKey。
   
5. 修改以上配置之后，就可以运行demo进行debug。    

6. demo的主要流程

    6.1 获取token：
      Boolean getToken(String clientid, String secret, String code).
      接口会返回比较重要的信息入accessToken 、 uid 等等。
      
    6.2 获取mqtt相关信息：
      boolean getMqttConfig(String clientid, String secret, String accessToken).
      返回的信息主要用于登录mqtt服务器。主要包含服务器地址、端口、用户名和密码等信息。
      
    6.3 获取设备webrtc相关配置：
      boolean getWebrtcConfig(String clientid, String secret, String accessToken, String deviceid).
      
    6.4 连接mqtt服务器：
  
    6.5 mqtt连接成功之后订阅相应的topic，topic的定义参见demo。
  
    6.6 订阅成功之后本地开启peerconnection，然后就可以通过mqtt进行sdp交互工作。
  
    6.7 交互成功之后就可以看到摄像头的视频。
    
## 文档


## 最新版本
