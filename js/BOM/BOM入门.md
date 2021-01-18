[TOC]
## window
- 窗口位置 screenLeft  srceenTop 
- 窗口操作(存在安全限制) moveTo moveBy open close resizeTo 
- 窗口大小 outerHeight outerWidth 
- 视口viewport大小  innerWidth innerHeight
- 视口位置 scrollBy scrollTo
- 对话框 alert confirm prompt

## location
- 处理Url  会用到URLSearchParams

## navigator
- 获取用户设备信息 platform userAgent oscpu vendor

## userAgent
- 可以做浏览器、设备识别，适配不同页面 可以用uaprase.js解析

## screen
- 显示器信息

## history
```typescript
interface History {
    readonly length: number;
    scrollRestoration: ScrollRestoration;
    readonly state: any;
    back(): void;
    forward(): void;
    go(delta?: number): void;
    pushState(data: any, title: string, url?: string | null): void;
    replaceState(data: any, title: string, url?: string | null): void;
}
```

  

