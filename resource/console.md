[http://www.cnblogs.com/Wayou/p/chrome-console-tips-and-tricks.html](http://www.cnblogs.com/Wayou/p/chrome-console-tips-and-tricks.html)
# 显示信息的命令
```html
<!DOCTYPE html>
<html>
<head>
    <title>常用console命令</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head>
<body>
    <script type="text/javascript">
        console.log('hello');
       console.info('信息');
       console.error('错误');
       console.warn('警告');
   </script>
</body>
</html>
```
最常用的就是console.log了。

# 占位符
console上述的集中度支持printf的占位符格式，支持的占位符有：字符（%s）、整数（%d或%i）、浮点数（%f）和对象（%o）。
```html
<script type="text/javascript">
        console.log("%d年%d月%d日",2011,3,26);
</script>
```
![](https://cloud.githubusercontent.com/assets/7871813/17443543/c10e7578-5b6d-11e6-9fe6-b9574597515a.png)

# 信息分组
```html
<!DOCTYPE html>
<html>
<head>
    <title>常用console命令</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head>
<body>
  <script type="text/javascript">

      console.group("第一组信息");
    　　　　console.log("第一组第一条:我的博客(http://www.ido321.com)");
    　　　　console.log("第一组第二条:CSDN(http://blog.csdn.net/u011043843)");
    　　console.groupEnd();

　　    console.group("第二组信息");
    　　　　console.log("第二组第一条:程序爱好者QQ群： 259280570");
    　　　　console.log("第二组第二条:欢迎你加入");
　　    console.groupEnd();

    </script>
</body>
</html>
```
![](https://cloud.githubusercontent.com/assets/7871813/17443563/d824b86c-5b6d-11e6-83fa-e623693d3118.png)

# 查看对象的信息
console.dir()可以显示一个对象所有的属性和方法。
```html
<script type="text/javascript">
        var info = {
            blog:"http://www.ido321.com",
            QQGroup:259280570,
            message:"程序爱好者欢迎你的加入"
        };
        console.dir(info);
</script>
```
![](https://cloud.githubusercontent.com/assets/7871813/17443571/e6d04f34-5b6d-11e6-9ed0-6b64afd5587a.png)

# 显示某个节点的内容
console.dirxml()用来显示网页的某个节点（node）所包含的html/xml代码。
```html
<!DOCTYPE html>
<html>
<head>
    <title>常用console命令</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head>
<body>
  <div id="info">
      <h3>我的博客：www.ido321.com</h3>
        <p>程序爱好者:259280570,欢迎你的加入</p>
    </div>
    <script type="text/javascript">
        var info = document.getElementById('info');
        console.dirxml(info);
    </script>
</body>
</html>
```

# 判断变量是否是真
console.assert()用来判断一个表达式或变量是否为真。如果结果为否，则在控制台输出一条相应信息，并且抛出一个异常。
```html
<script type="text/javascript">
    　　var result = 1;
    　　console.assert( result );
    　　var year = 2014;
    　　console.assert(year == 2018 );
</script>
```
1是非0值，是真；而第二个判断是假，在控制台显示错误信息
![](https://cloud.githubusercontent.com/assets/7871813/17443601/0c202f34-5b6e-11e6-9b50-ce0cbc843ea5.png)

# 追踪函数的调用轨迹
console.trace()用来追踪函数的调用轨迹。
```html
<script type="text/javascript">
    /*函数是如何被调用的，在其中加入console.trace()方法就可以了*/
　　function add(a,b){
        console.trace();
　　　　return a+b;
　　}
　　var x = add3(1,1);
　　function add3(a,b){return add2(a,b);}
　　function add2(a,b){return add1(a,b);}
  　function add1(a,b){return add(a,b);}
</script>
```
![](https://cloud.githubusercontent.com/assets/7871813/17443612/1b91bf50-5b6e-11e6-8bb8-2441435521bf.png)

# 计时功能
console.time()和console.timeEnd()，用来显示代码的运行时间。
```html
<script type="text/javascript">
　　console.time("控制台计时器一");
　　for(var i=0;i<1000;i++){
　　　　for(var j=0;j<1000;j++){}
　　}
　　console.timeEnd("控制台计时器一");
</script>
```
运行时间是38.84ms
![](https://cloud.githubusercontent.com/assets/7871813/17443620/28b45d3c-5b6e-11e6-9cf4-f4fc7c6b84bf.png)

# console.profile()的性能分析
性能分析（Profiler）就是分析程序各个部分的运行时间，找出瓶颈所在，使用的方法是console.profile()。
```html
<script type="text/javascript">
    function All() {
        alert(11);
        for (var i = 0; i < 10; i++) {
            funcA(1000);
        }
        funcB(10000);
    }

    function funcA(count) {
        for (var i = 0; i < count; i++) {}
    }

    function funcB(count) {
        for (var i = 0; i < count; i++) {}
    }
    console.profile('性能分析器');
    All();
    console.profileEnd();
</script>
```
![](https://cloud.githubusercontent.com/assets/7871813/17443637/438c79b4-5b6e-11e6-896a-5d9a0c5da63d.png)