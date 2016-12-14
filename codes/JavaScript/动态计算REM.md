
# [使用Flexible实现手淘H5页面的终端适配](http://www.w3cplus.com/mobile/lib-flexible-for-html5-layout.html)

[https://github.com/amfe/lib-flexible](https://github.com/amfe/lib-flexible)

# 动态计算 rem 基准大小
```js
/**
 * 动态计算 rem 基准大小
 */
!(function(doc, win) {
    var docEle = doc.documentElement,
        evt = "onorientationchange" in window ? "orientationchange" : "resize",
        fn = function() {
            var width = docEle.clientWidth;
            width && (docEle.style.fontSize = 20 * (width / 320) + "px");
        };
     
    win.addEventListener(evt, fn, false);
    doc.addEventListener("DOMContentLoaded", fn, false);
 
}(document, window));
```

> `任意浏览器的默认字体高都是16px`。所有未经调整的浏览器都符合: 1em=16px。那么12px=0.75em,10px=0.625em。为了简化font-size的换算，需要在css中的body选择器中声明Font-size=62.5%，这就使em值变为 16px*62.5%=10px, 这样12px=1.2em, 10px=1em, 也就是说只需要将你的原来的px数值除以10，然后换上em作为单位就行了。

```css
html { font-size: 62.5%;/*10 ÷ 16 × 100% = 62.5%*/ } 
body { font-size: 1.4rem;/*1.4 × 10px = 14px */ }
h1 { font-size: 2.4rem;/*2.4 × 10px = 24px*/ }
p {font-size:14px; font-size:1.4rem;}/*IE8及之前版本的IE浏览器使用14像素*/
```


# 下面列出几种常见设计稿相应的font-size值：
> deviceWidth = 320，font-size = 320 / 6.4 = 50px
> deviceWidth = 375，font-size = 375 / 6.4 = 58.59375px
> deviceWidth = 414，font-size = 414 / 6.4 = 64.6875px
> deviceWidth = 500，font-size = 500 / 6.4 = 78.125px 

**也可使用JS计算**:
```js
(function () {
    document.addEventListener('DOMContentLoaded', function () {
        var html = document.documentElement;
        var windowWidth = html.clientWidth;
        html.style.fontSize = windowWidth / 6.4 + 'px';
        // 等价于html.style.fontSize = windowWidth / 640 * 100 + 'px';
    }, false);
})();
// 这个6.4就是根据设计稿的横向宽度来确定的，假如你的设计稿是750
// 那么 html.style.fontSize = windowWidth / 7.5 + 'px';
```
[webapp font-size解决问题的方案 ](http://blog.csdn.net/huang100qi/article/details/49886713)