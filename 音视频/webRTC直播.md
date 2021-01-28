[TOC]

## webRTC直播原理
1. 获取token
2. 登录房间
3. 获取房间用户列表
4. 服务端流更新回调
5. 获取webrtc_url地址
6. 心跳保证房间不销毁（30秒一次）

![image-20210127181600818](https://tva1.sinaimg.cn/large/008eGmZEgy1gn2f5xd0suj311s0gaqb2.jpg)

## 流媒体 StreamMedia
## video推流
video.srcObject = {
    active: true
    id: "kbBS3BIQFoi5li1BdWISCr3fon4PK1mvnQFB"
    onactive: null
    onaddtrack: null
    oninactive: null
    onremovetrack: null
}

## video拉流
video.srcObject = {
    active: true
    id: "8cd67b8b-b014-4dd8-8fcc-b6df06b420fe"
    onactive: null
    onaddtrack: null
    oninactive: null
    onremovetrack: null
}

```javascript
let context = {
  audio: {
    audioBitrate: 46.77236429642547,
    audioCodec: "opus",
    audioFPS: 50.00181484451666,
    audioJitter: 0.012,
    audioLevel: 0,
    audioPacketsLost: 0,
    audioPacketsLostRate: 0,
    audioQuality: 5,
    audioSamplingRate: 492.0399999996975,
    audioSendLevel: 19.16477463154686,
    googCodecName: "opus",
    muteState: "0"
  },
  codecImplementationName: "ExternalDecoder",
  currentRoundTripTime: 0.016,
  googAvailableSendBandwidth: "300000",
  muted: false,
  nackCount: 241,
  paused: true,
  playData: 0,
  pliCount: 2,
  sinkId: "",
  totalRoundTripTime: 2.859,
  video: {
    frameHeight: 240,
    frameWidth: 320,
    googCodecName: "H264",
    muteState: "0",
    videoBitrate: 303.37101102465147,
    videoFPS: 15.000544453354996,
    videoFramesDecoded: 7317,
    videoFramesDropped: 0,
    videoPacketsLost: 0,
    videoPacketsLostRate: 0,
    videoQuality: 5,
    videoTransferFPS: 15.000544453354996
  },
  volume: 1
}
```


## 参考
- [zego demo](https://zegodev.github.io/zego-express-webrtc-sample/base/index.html)
- [zego 开发者中心](https://doc-zh.zego.im/zh/3546.html)
