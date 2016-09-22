
# 下载
1. 登录[http://httpd.apache.org/download.cgi](http://httpd.apache.org/download.cgi) 这个地址
    ![](http://hiphotos.baidu.com/exp/pic/item/734f12f3d7ca7bcbd94cbcbebd096b63f624a829.jpg)
2. 进入如下界面后，选择第一项`ApacheHaus`，这是个第三方下载平台，在它的网站下载独立的Apache会是一个压缩包，第二项也是独立的Apache下载地址，另外三个是集成开发环境。
    ![](http://hiphotos.baidu.com/exp/pic/item/8cf0d51349540923ed2106ef9158d109b2de4993.jpg)
3. 在下载界面中，会发现VC9和VC11字样，通过阅读相关内容得知:
    - VC9是指用VS2008编译的
    - VC11是指用VS2012编译的，**VC11无法在windows xp和server 2003中使用**
    ![](http://hiphotos.baidu.com/exp/pic/item/c9d4cf43ad4bd1130b07d6a359afa40f4afb051d.jpg)

# 配置
- 进入解压后的Apache目录，找到 `~\Apache\conf\httpd.conf` 文件并用编辑器打开
- 找到 `Define SRVROOT` ，将后面的地址改成本地Apache安装存放的地址，例如:
    ```
    Define SRVROOT "c:/PortableSoft/Apache"
    ```
- 找到 `Listene 80` ，若80端口被占用（可在cmd下用命令 `netstat -a` 查看），则将80端口改为别的
- 找到 `DocumentRoot`，将后面的地址修改为需要的wwwroot
- 找到 `DirectoryIndex `，将后面的文件修改为需要的默认启动页面

# 安装主服务
- 管理员打开CMD窗口，输入：
    ```
    "c:\PortableSoft\Apache\bin\httpd.exe" -k install -n apache
    ```
    > **带有引号的**。
    > 该命令的意思是，安装 apache 服务，并将该服务名称命名为apache(也可以改成别的)
- Win+R运行输入 `services.msc`，找到刚刚安装的 apache 服务，右键属性中将`启动类型`设置为`手动`
- 进入 Apache 安装目录，找到`c:\PortableSoft\Apache\bin\ApacheMonitor.exe`，运行后在系统右下角状态栏中打开窗口界面点击`Start`启动服务

# 卸载
1. 停止 Apache 服务
2. 管理员打开CMD窗口，输入:
    ```
    sc delete apache
    ```

# 参考
- [Apache 修改端口 默认路径配置修改方法](http://blog.csdn.net/lantianzhange/article/details/8594215)