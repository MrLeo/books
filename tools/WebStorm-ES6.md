# WebStorm ES6 语法支持设置

在webstorm写下了这段代码，体验一下ES6语法的便利，但是一大堆报错
![](http://upload-images.jianshu.io/upload_images/436630-e162440fc4554a14.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 语法支持设置

> Preferences > Languages & Frameworks > JavaScript

这里只要配置ECMAScript版本即可

![Preferences > Languages & Frameworks > JavaScript](http://upload-images.jianshu.io/upload_images/436630-0fac0723fbae8d81.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 自动转码为ES5

> file watcher + [babel](http://babeljs.io/)（ES6转码器）

1. `npm install -g babel-cli` / `npm install --save-dev babel-cli`
2. Preferences > Tools > File watchers
3. 点击“+”按钮
    ![](http://upload-images.jianshu.io/upload_images/436630-187656ec1bf208c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
    > **File Type**：配置该监听器监听的文件类型，可以在Preferences > Editor > File types中配置
    > **Scope**：配置该监听器的监听范围，可自定义新的范围，也可以使用Preferences > Appearance & Behavior > Scopes
    > **Program**：babel的安装位置
    > `C:\Users\lxbin\node_modules\.bin\babel.cmd`
    > **Arguments**：命令执行参数，参见Babel CLI
    > `$FilePathRelativeToProjectRoot$ --out-dir dist --source-maps  --presets es2015`
    > **Working directory**：babel命令执行的位置，默认为文件所在目录
    > `dist\$FileDirRelativeToProjectRoot$\$FileNameWithoutExtension$.js:dist\$FileDirRelativeToProjectRoot$\$FileNameWithoutExtension$.js.map`

4. 最后在项目目录下面添加一个`.babelrc`文件
    ```json
    {
      "presets": ["es2015"]
    }
    ```