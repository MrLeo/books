# Caddy 服务器

> 这是一个Web Server的时代，[apache](http://httpd.apache.org/)与[nginx](http://nginx.org/)共舞，在追求极致性能的路上，没有最高，只有更高。但这又是一个追求个性化的时代，有些Web Server并没有去挤“Performance提升”这一独木桥，而是有着自己的定位，Caddy就是这样一个开源Web Server。

> Caddy的作者Matt Holt在[caddy官网](http://caddyserver.com/)以及FAQ中对caddy的目标阐释如下： 其他Web Server为Web而设计，Caddy为human设计。功能定位上，与经常充当最前端反向代理的nginx不同，caddy致力于成为一个易用的静态 文件Web Server。可以看出Caddy主打易用性，使用配置简单。并且得益于Go的跨平台特性，caddy很容易的支持了三大主流平台:Windows、 Linux、Mac。在Caddy开发者文档中，我们可以看到caddy还可以在Android(linux arm)上运行。caddy目前版本为0.7.1，还不稳定，且后续版本可能变化较大，甚至与前期版本不兼容，因此作者目前不推荐caddy在生产环境被 重度使用。

> Caddy 是一个支持 HTTP/2 的跨平台 Web 服务器，使用和配置都非常简单。Caddy 支持 HTTP/2, IPv6, Markdown, WebSockets, FastCGI, 模板等等。

- iplaysoft介绍的[《轻松把文件夹变成网站！使用 Caddy 服务器软件自己搭建网页形式的文件共享》](http://www.iplaysoft.com/caddy.html)
- 小众软件[《Caddy – 最简单的支持 HTTP/2 的网页服务器》](http://www.appinn.com/caddy-server/)

## 我的一些配置信息
[《Caddyfile配置官网说明》](https://caddyserver.com/docs/caddyfile)
```bat
#=> Caddyfile配置 https://caddyserver.com/docs/caddyfile
##########################
#          多站点         #
##########################
#=> Vue2.0站点 → port:2000
localhost:2000, 
http://vue-2-demo.com {
    # 站点物理路径
    root ../../../Users/lxbin/Documents/WWW/vue-2.0-demo/dist
    # log日志输出路径
    #log ../log/localhost-2000.log 
    # 开启gzip
    #gzip 
}

#=> 9X_WAP站点 → port:8000
localhost:8000,
http://m2.test.jiuxiulvxing.com {
    # 站点物理路径
    root ../../../Users/lxbin/Documents/WWW/9X_WAP/
    # log日志输出路径
    log ../log/localhost-8000.log 
    # 开启gzip
    #gzip 
}

##########################
#         反向代理        #
##########################
#=> 反向代理 → port:80
#http://leo.xuebin.leo {
#    proxy / localhost:80
#    log ../log/proxy-port-80.log 
#}

#=> 反向代理 → port:8080
#http://leo.xuebin.leo {
#    proxy / localhost:8080
#    log ../log/proxy-port-8080.log 
#}

#http://leo.xuebin.leo {
#    proxy / localhost:8000
#    log ../log/proxy-port-8000.log 
#}

##########################
#        文件服务器       #
##########################
#=> 文件服务器,指定文件服务器地址
192.168.100.126:1000
filemanager / {
    # 文件目录地址
    show        ../../../Users/lxbin/Documents/WWW/
    # 是否可以新建
    allow_new   true
    # 是否可以修改
    allow_edit  true
}

##########################
#        异常处理         #
##########################
errors {
    log ../log/error.log
    404 404.html # Not Found
    500 500.html # Internal Server Error
}
```