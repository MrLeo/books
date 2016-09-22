```css
body {
    /*使用无衬线字体*/
    font-family: "Helvetica Neue", Helvetica, STHeiTi, sans-serif; 
}

a, img {
    /*禁止长按链接与图片弹出菜单*/
    -webkit-touch-callout: none; 
}

html, body {
    /*禁止选中文本*/
    -webkit-user-select: none; 
    user-select: none;
}

button,input,optgroup,select,textarea {
    /*去掉webkit默认的表单样式*/
    -webkit-appearance:none; 
}

a,button,input,optgroup,select,textarea {
    /*去掉a、input和button点击时的蓝色外边框和灰色半透明背景*/
    -webkit-tap-highlight-color:rgba(0,0,0,0); 
}

input::-webkit-input-placeholder {
    /*修改webkit中input的planceholder样式*/
    color:#ccc; 
}

input:focus::-webkit-input-placeholder {
    /*修改webkit中focus状态下input的planceholder样式*/
    color:#f00; 
}

body {
    /*禁止IOS调整字体大小*/
    -webkit-text-size-adjust: 100%!important; 
}

input::-webkit-input-speech-button {
    /*隐藏Android的语音输入按钮*/
    display: none; 
}
```