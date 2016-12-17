---
title:前端调试解决方案
---

[TOC]

# 真机联调

## [vConsole](https://github.com/WechatFE/vConsole/blob/dev/README_CN.md)
> `腾讯`出品的一个轻量、可拓展、针对手机网页的前端开发者调试面板。
> **与 [vConsole](https://github.com/WechatFE/vConsole/blob/dev/README_CN.md) 类似的还有 [Eruda](https://github.com/liriliri/eruda)、[JSConsole](https://jsconsole.com/)**

- 查看 console 日志
- 查看网络请求
- 手动执行 JS 命令行
- 自定义插件

```js
//建议通过url参数来控制是否加载调试器，例↓
;(function () {
    var src = '//liriliri.github.io/eruda/eruda.min.js';
    if (!/eruda=true/.test(window.location) && localStorage.getItem('active-eruda') != 'true') return;
    document.write('<scr' + 'ipt src="' + src + '"></scr' + 'ipt>');
    document.write('<scr' + 'ipt>eruda.init();</scr' + 'ipt>');
})();
```

## [spy-debugger](https://github.com/wuchangming/spy-debugger)

> 一站式页面调试、抓包工具。远程调试任何手机浏览器页面，任何手机移动端webview（如：微信，HybirdApp等）HTTP/HTTPS
> **与[spy-debugger](https://github.com/wuchangming/spy-debugger)类似的还有[whistle](https://github.com/avwo/whistle)**

1. 页面调试＋抓包。
3. 支持HTTPS。
4. spy-debugger内部集成了weinre、node-mitmproxy、AnyProxy。
5. 自动忽略原生App发起的https请求，只拦截webview发起的https请求。对使用了SSL pinning技术的原生App不造成任何影响。
6. 可以配合其它代理工具一起使用(默认使用AnyProxy) (设置外部代理)

**spy-debugger 截图**
![使用spy-debugger调试样式](https://raw.githubusercontent.com/wuchangming/spy-debugger/master/demo/img/demo.png)
![使用spy-debugger抓包](https://raw.githubusercontent.com/wuchangming/spy-debugger/master/demo/img/AnyProxy.png)
**whistle 截图**
![whistle基本功能](https://raw.githubusercontent.com/avwo/whistleui/master/assets/functions.png)
![whistle抓包](https://raw.githubusercontent.com/avwo/whistleui/master/img/network.gif)
![whistle rules](https://raw.githubusercontent.com/avwo/whistleui/master/img/rules.gif)
![whistle values](https://raw.githubusercontent.com/avwo/whistleui/master/img/values.gif)

# 多设备自适应开发与调试

## [Browsersync](http://www.browsersync.cn/)
> **多设备同步操作。**
> Browsersync能让浏览器实时、快速响应您的文件更改（html、js、css、sass、less等）并自动刷新页面。更重要的是 `Browsersync可以同时在PC、平板、手机等设备下进项调试`。您可以想象一下：“假设您的桌子上有pc、ipad、iphone、android等设备，同时打开了您需要调试的页面，当您使用browsersync后，您的任何一次代码保存，以上的设备都会同时显示您的改动”。无论您是前端还是后端工程师，使用它将提高您30%的工作效率。

## [Blisk浏览器](https://blisk.io/)
- 完全模拟手机和平板电脑的内部
- 网址和桌面和移动的滚动是同步的
- 文件更改会自动刷新页面
- 可通过DevTools调试桌面和移动效果
- Blisk 适用于任何IDE、语言和框架
![](https://img.cmhello.com/2016/06/blisk.jpg)