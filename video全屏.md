## video在各个浏览器中全屏
```css
<video id="video" webkit-playsinline="" playsinline="" rate="1" class="m-player hideControls" src="blob:https://m.iqiyi.com/7671f2f0-fa69-4b54-91df-d35381c3ed54"></video>

video{
	object-fill:contain
}
```

- 在QQ浏览器和微信中不能全屏 QQ浏览器和微信用的都是X5内核
- video全屏有些手机可以自动旋转，有些要开启旋转
- QQ浏览器 微信浏览器对WebRTC兼容不好



