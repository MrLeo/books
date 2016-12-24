```css
/*使用无衬线字体*/
body {
    font-family: "Helvetica Neue", Helvetica, STHeiTi, sans-serif; 
}

/*禁止长按链接与图片弹出菜单*/
a, img {
    -webkit-touch-callout: none; 
}

/*禁止选中文本*/
html, body {
    -webkit-user-select: none; 
    user-select: none;
}

/* 如何禁止选中文字 */
.noselect {
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Chrome/Safari/Opera */
    -khtml-user-select: none; /* Konqueror */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */
    user-select: none; /* Non-prefixed version, currently not supported by any browser */
}

/*去掉webkit默认的表单样式*/
button,input,optgroup,select,textarea {
    -webkit-appearance:none; 
}

/*去掉a、input和button点击时的蓝色外边框和灰色半透明背景*/
a,button,input,optgroup,select,textarea {
    -webkit-tap-highlight-color:rgba(0,0,0,0); 
}

/*修改webkit中input的planceholder样式*/
input::-webkit-input-placeholder {
    color:#ccc; 
}

/*修改webkit中focus状态下input的planceholder样式*/
input:focus::-webkit-input-placeholder {
    color:#f00; 
}

/*禁止IOS调整字体大小*/
body {
    -webkit-text-size-adjust: 100%!important; 
}

/*隐藏Android的语音输入按钮*/
input::-webkit-input-speech-button {
    display: none; 
}
```