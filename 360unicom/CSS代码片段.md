### 以下是常用的代码收集，没有任何技术含量，只是填坑的积累。转载请注明出处，谢谢。

#### 1. css 2.x
- 文字换行
```css
/*强制不换行*/
white-space:nowrap;
/*自动换行*/
word-wrap: break-word;
word-break: normal;
/*强制英文单词断行*/
word-break:break-all;
```

- 两端对齐
```css
text-align:justify;text-justify:inter-ideogra
```

- [去掉Webkit(chrome)浏览器中input(文本框)或textarea的黄色焦点框](http://www.cnblogs.com/niao/archive/2012/09/07/2674511.html)
```css
input,button,select,textarea{ outline:none;}
textarea{ font-size:13px; resize:none;}
```

- [去掉chrome记住密码后自动填充表单的黄色背景](http://www.tuicool.com/articles/EZ777n )

- ie6: position:fixed
```css
.fixed-top /* position fixed Top */{position:fixed;bottom:auto;top:0; }
* html .fixed-top /* IE6 position fixed Top */{position:absolute;bottom:auto;top:expression(eval(document.documentElement.scrollTop));}
*html{background-image:url(about:blank);background-attachment:fixed;}
```

- clearfix
```css
.clearfix:after{visibility:hidden;display:block;font-size:0;content:" ";clear:both;height:0;}
.clearfix{display:inline-block;}
html[xmlns] .clearfix{display:block;}
* html .clearfix{height:1%;}

.clearfix{*zoom: 1;}
.clearfix:after{clear:both;display:table;content:"”;}

.clearfix{overflow:hidden;_zoom:1;}
```
[http://www.daqianduan.com/3606.html](http://www.daqianduan.com/3606.html)

- seperate-table
```css
.tab{border-collapse:separate;border:1px solid #e0e0e0;}
.tab th,.tab td{padding:3px;font-size:12px;background:#f5f9fb;border:1px solid;border-color:#fff #deedf6 #deedf6 #fff;}
.tab th{background:#edf4f0;}
.tab tr.even td{background:#fff;}
```
```html
<table class="tab" width="100%" cellpadding="0" cellspacing="0" border="0">
    <tr>
        <th>111</th>
        <td>222</td>
    </tr>
    <tr>
        <th>111</th>
        <td>222</td>
    </tr>
</table>
```

- min-height: 最小高度兼容代码
```css
.minheight500{min-height:500px;height:auto !important;height:500px;overflow:visible;}
```
- 鼠标不允许点击
```css
cursor:not-allowed;
```
- mac font: osx平台字体优化
```css
font-family:"Hiragino Sans GB","Hiragino Sans GB W3",'微软雅黑';
```

- 文字过多后显示省略号
```css
.ellipsis,.ell{white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
```

#### 2. css 3

- 投影
```css
.b{box-shadow:inset 1px -1px 0 #f1f1f1;text-shadow:1px 1px 0px #630;}
filter:progid:DXImageTransform.Microsoft.gradient(enabled='true',startColorstr='#99000000',endColorstr='#99000000');background:rgba(0,0,0,.6);

background:rgba(0,0,0,0.5);filter:progid:DXImageTransform.Microsoft.gradient(GradientType=0,startColorstr='#50000000',endColorstr='#50000000')\9;
```
- [search占位](http://www.qianduan.net/search-box-style-custom-webkit.html)
```css
::-webkit-input-placeholder {}
::-moz-input-placeholder {}
input:focus::-webkit-input-placeholder { color: transparent; }
-webkit-appearance:none;  google边框去除
input[type="search"]{-webkit-appearance:textfield;} // 去除chrome默认样式
http://i.wanz.im/2011/02/04/remove_border_from_input_type_search/
http://blog.csdn.net/do_it__/article/details/6789699
line-height: normal; /* for non-ie */
line-height: 22px\9; /* for ie */
```
- title 换行
```html
&#13;
```

- 关闭 x 符号
```html
&#215;
```

- [全部浏览器的兼容代码生成](http://www.colorzilla.com/gradient-editor/ )
[CSS 实现 textArea 的 placeholder 换行](http://segmentfault.com/a/1190000000362621)

- 阻止默认事件
```css
pointer-events:none;
```
- 变灰 gray
```css
html{
    filter: grayscale(100%);
    -webkit-filter: grayscale(100%);
    -moz-filter: grayscale(100%);
    -ms-filter: grayscale(100%);
    -o-filter: grayscale(100%);
    filter: url("data:image/svg+xml;utf8,<svg xmlns=\'http://www.w3.org/2000/svg\'><filter id=\'grayscale\'><feColorMatrix type=\'matrix\' values=\'0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0 0 0 1 0\'/></filter></svg>#grayscale");
    filter:progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
    -webkit-filter: grayscale(1);
}
```
- firefox 阻止选中
```css
-moz-user-focus:ignore;-moz-user-input:disabled;-moz-user-select:none;
```
- 箭头
```css
display:block;border:solid transparent;line-height: 0;width:0; height:0;border-top:solid #0288ce;border-width:8px 6px 0 6px;

border-style:solid; border-width:7px; border-color:transparent transparent transparent #ff7020;
position:absolute;top: 0;left: 0;border-width:20px;border-style:solid;border-color:#d1ddde transparent transparent #d1ddde;
```
ie6 bug测试，把border-style设为dashed.

- 取消textarea右下角可拖动手柄
```css
resize:none
```
- 取消chrome form表单的聚焦边框
```css
input,button,select,textarea{outline:none}
textarea{resize:none}
```
- 取消a链接的黄色边框
```css
a{-webkit-tap-highlight-color:rgba(0,0,0,0);}
```
- webkit 水平居中
```css
display:-webkit-box;-webkit-box-pack:center; -webkit-box-align: center;
```
- 取消chrome 搜索x提示
```css
input[type=search]::-webkit-search-decoration,
input[type=search]::-webkit-search-cancel-button,
input[type=search]::-webkit-search-results-button,
input[type=search]::-webkit-search-results-decoration {
    display: none;
}
```
- [chrome取消默认黄色背景](http://stackoverflow.com/questions/2338102/override-browser-form-filling-and-input-highlighting-with-html-css)
```css
input:-webkit-autofill {-webkit-box-shadow: 0 0 0px 1000px white inset;}
input:-webkit-autofill,
textarea:-webkit-autofill,
select:-webkit-autofill {
    -webkit-box-shadow: 0 0 0 1000px white inset;
}
autocomplete="off"
```
- 手机版本网页a标记虚线框问题
```css
a:focus {outline:none;-moz-outline:none;}
```
- 焦点去除背景
```css
-webkit-tap-highlight-color:rgba(255, 255, 255, 0);
-webkit-tap-highlight-color:transparent;  // i.e. Nexus5/Chrome and Kindle Fire HD 7''
```
- placeholder占位符颜色自定义
```css
input:-moz-placeholder {color: #369;}
::-webkit-input-placeholder {color:#369;}
```

- [IOS 禁用高亮](http://hi.barretlee.com/2014/03/31/tap-highlight-in-webview/)
```css
-webkit-tap-highlight-color:rgba(255,0,0,0.5);-webkit-tap-highlight-color:transparent; /* For some Androids */
```

- [用户不能选择元素中的任何内容](http://www.qianduan.net/introduce-user-select/)
```css
user-select:none
```

- IOS iframe 滚动 [滚动回弹特效](http://www.cnblogs.com/flash3d/archive/2013/09/28/3343877.html)
```css
-webkit-overflow-scrolling:touch;overflow-y:scroll;
```

- [禁止选中文本](http://www.qianduan.net/introduce-user-select/)
```css
-moz-user-select:none;
-webkit-user-select:none;
-ms-user-select:none;
user-select:none;
```
- [模糊(毛玻璃)效果1](http://www.zhangxinxu.com/wordpress/2013/11/%E5%B0%8Ftip-%E4%BD%BF%E7%94%A8css%E5%B0%86%E5%9B%BE%E7%89%87%E8%BD%AC%E6%8D%A2%E6%88%90%E6%A8%A1%E7%B3%8A%E6%AF%9B%E7%8E%BB%E7%92%83%E6%95%88%E6%9E%9C/)
- [模糊(毛玻璃)效果2](http://mao.li/css3-blur-filter-pratice/)
- [模糊(毛玻璃)逼真效果](http://codepen.io/ariona/pen/geFIK)
```css
.blur {    
    -webkit-filter: blur(10px); /* Chrome, Opera */
       -moz-filter: blur(10px);
        -ms-filter: blur(10px);    
            filter: blur(10px);    
}
```
```html
<img src="mm1.jpg" />
<img src="mm1.jpg" class="blur" />
```

- 显示旋转加载图片，[下拉加载数据](https://github.com/chalecao/chale/blob/master/iscroll.js)
```css
#pullDown .pullDownIcon{display:inline-block;vertical-align:middle;width:40px;height:40px;background:url(https://github.com/chalecao/chale/blob/master/pull-icon%402x.png) 0 0 no-repeat;-webkit-background-size:40px 80px;background-size:40px 80px;-webkit-transition-property:-webkit-transform;-webkit-transition-duration:250ms}
#pullDown .pullDownIcon{-webkit-transform:rotate(0deg) translateZ(0)}
#pullDown .pullDownLabel{display:inline-block;vertical-align:middle;margin-left:5px;}
#pullDown.flip .pullDownIcon{-webkit-transform:rotate(-180deg) translateZ(0)}
#pullDown.loading .pullDownIcon{background-position:0 100%;-webkit-transform:rotate(0deg) translateZ(0);-webkit-transition-duration:0ms;-webkit-animation-name:loading;-webkit-animation-duration:2s;-webkit-animation-iteration-count:infinite;-webkit-animation-timing-function:linear}
@-webkit-keyframes loading{
    from{-webkit-transform:rotate(0deg) translateZ(0)}
    to{-webkit-transform:rotate(360deg) translateZ(0)}
}

```

```html
<div id="pullDown" class="none loading">
    <span class="pullDownIcon"></span><span class="pullDownLabel">正在载入中...</span>
</div>
```


