```typescript

let res  = await fetch('https://account.wps.cn/libs/img/v1/syncloginstatus/icon_warning.ec5b819b.svg')
let blob = await res.blob();
// 序列化
let blobStr = await blob.text();
// 反序列化
let blob2 = new Blob([blobStr], {type: blob.type })

```
