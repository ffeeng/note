[TOC]
![image-20210220153221693](https://tva1.sinaimg.cn/large/008eGmZEgy1gnwd9trbjlj30r00cugm3.jpg)
![时序图](https://tva1.sinaimg.cn/large/008eGmZEgy1gnwd9m4bejj30y40u07an.jpg)



### [web直播](https://doc-zh.zego.im/zh/7638.html)

- WebRTC  采集传输 STUN(Session Traversal Utilities for NAT, TURN ChannelData Message)
- video   播放 
- 流媒体服务器  处理
- webSocket（ZegoExpressWebRTC-sdk） 发房间消息 在线人数

#### 实现原理
- 采集 
- 预览
- 传输 推流
- 显示 拉流
- 最小原型
```javascript
let constraints = { audio: true, video: { width: 1280, height: 720 } };
// 视频采集
const mediaStream = await navigator.mediaDevices.getUserMedia(constraints)                                                                          
// 预览
video.srcObject = mediaStream;
video.onloadedmetadata = function(e) {
    video.play();
};
// 传输 WebRTC todo 
// 显示
video.srcObject = remoteStream;
```


#### 实现步骤
1. 登录房间
2. 推流  
3. 流更新获取拉流地址
```javascript
await zg.loginRoom(this.data.roomID, this.data.token, {userID: this.data.userID, userName: 'nick' + this.data.userID});
// 获取推流地址
const {url} = await zg.startPublishingStream(context.data.pushStreamID);
// 推流到服务启后触发流更新 从streamList中拿到拉流src
zg.on("roomStreamUpdate", (roomID, updateType, streamList) => {
  // ... 解析出 remoteStream
  video.srcObject = remoteStream
});
```


### demo
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>WebRTC直播</title>
  <script src="./ZegoExpressWebRTC-2.1.0.js"></script>
</head>
<body>
<video id="local-video" autoplay width="500px" height="500px"></video>
<video id="remote-video" autoplay width="500px" height="500px"></video>

<script>
  (async () => {
    try {
      let appID = 173****9272****706; // 请从官网控制台获取对应的appID
      let server = 'wss://webliveroom-test.zego.im/ws'; // 请从官网控制台获取对应的server地址，否则可能登录失败
      const userId = '1';
      const zg = new ZegoExpressEngine(appID, server);
      // console.log(zg)
      let url = 'https://wsliveroom-alpha.zego.im:8282/token';
      const query = new URLSearchParams({
        app_id: appID,
        id_name: userId
      });
      url = url + '?' + query.toString();
      // url = 'https://wsliveroom-alpha.zego.im:8282/token?app_id=1739272706&id_name=sample1613981824652'
      const res = await fetch(url);
      const token = await res.text();

      const result = await zg.loginRoom('2', token, {
        userID: userId,
        userName: 'feng'
      });
      console.warn({result})

      let constraints = {
        camera: {
          AEC: true,
          AGC: true,
          ANS: true,
          audio: true,
        }
      }
      const localStream = await zg.createStream(constraints);
      let localVideo = document.getElementById('local-video');
      let remoteVideo = document.getElementById('remote-video');
      localVideo.srcObject = localStream;
      // localStream 为创建流获取的 MediaStream 对象
      let t = zg.startPublishingStream('stream002', localStream)
      console.warn('publish stream' , t);


      zg.on('publisherStateUpdate',async result => {
        console.warn('publisherStateUpdate',result);
        const remoteStream = await zg.startPlayingStream(result.streamID);
        // remoteVideo为本地<video>或<audio>对象
        remoteVideo.srcObject = remoteStream;
        // 推流状态更新回调
        // ...
      })

      zg.on('publishQualityUpdate', (streamID, stats) => {
        console.warn('publishQualityUpdate',result);
        // 推流质量回调
        // ...
      })
    } catch (e) {
      console.error(e);
    }
  })();

</script>
</body>
</html>
```

## 参考
- [直播实现流程](https://doc-zh.zego.im/zh/7638.html)
- [webrtc demo](https://zegodev.github.io/zego-express-webrtc-sample/)
