# 前端开发资源汇总

* [Web前端资源](Web前端.md) 
* [CSS代码片段](CSS代码片段.md)
* [JS代码片段](JS代码片段.md)
* [HBuilder](resource/HBuilder.md)

***
# UserScript

#### UserScript 介绍：
> UserScript 又称“油猴脚本”，其实就是一个在浏览器中能本地执行扩展名为`.user.js`的js文件，使用UserScript可以自定义被浏览的网页，更多详细可参考[维基百科](https://zh.wikipedia.org/wiki/Greasemonkey)中的介绍。


#### UserScript 优势：
> 在Chrome中，UserScript类似于一个精简的Chrome扩展，两者的区别在于Chrome扩展是在浏览器启动的时候就会执行，但UserScript是在使用的时才候执行，这样就大大减少了Chrome的内存占用。而且UserScript只是一个单纯的js文件，可以随意定制修改。


- [Chrome原生安装UserScript脚本](https://github.com/EchoFUN/melodycoder/issues/12)
- [Chrome油猴脚本管理插件 - TamperMonkey](https://chrome.google.com/webstore/detail/dhdgffkkebhmkfjojejmpbldmpobfkfo)
- [自定义油猴脚本模版](https://raw.githubusercontent.com/MrLeo/Leo.UserScript/master/README.md)
- 热门油猴脚本推荐：
    - [二维码生成](http://userscripts-mirror.org/scripts/source/185467.user.js)
    - [百度网盘下载助手](https://greasyfork.org/scripts/986-百度网盘助手/code/百度网盘助手.user.js)

- 油猴脚本搜索(根据受欢迎程度排列)：
    - [userscript官网](http://userscripts-mirror.org/)
    - [Greasy Fork](https://greasyfork.org/zh-CN)
    - [MonkeyGuts](https://monkeyguts.com/index.php?lang=zh)
    - [OpenUserJS.org](https://openuserjs.org/)
    - [User Script / 脚本](http://j.mozest.com/zh-CN/userscript/)
    - [油猴脚本|火狐范](http://www.firefoxfan.com/greasemonkey-scripts)
- [Greasemonkey API](http://old.sebug.net/paper/books/greasemonkey/)


#### Chrome userscript 模本

```js
// ==UserScript==
// @name            MyUserScript Template
// @namespace       https://github.com/MrLeo/Leo.UserScript
// @description     userscript for mr.leo
// @match           http://*/*
// @include         http://*/*
// @require         http://code.jquery.com/jquery-latest.js
// @updateURL       uploadFilePath.user.js
// @downloadURL     uploadFilePath.user.js
// @version         0.1
// ==/UserScript==

//根据传入的URL，在head里生成script引用DOM对象
function createScriptLink(url){
    var scriptElement = document.createElement('script');
    scriptElement.setAttribute('type', 'text/javascript');
    scriptElement.setAttribute('src', url);
    document.head.appendChild(scriptElement);
    console.log('[添加引用]', (new XMLSerializer()).serializeToString(scriptElement));
}
;(function(){
    //在head引入JQuery
    window.jQuery || createScriptLink('//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js')
    if($){$ = window.jQuery;}
    console.log('[leo]', `${$}`);
    
})();

```
