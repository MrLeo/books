
[Nginx配置杂记](https://wenjs.me/p/note-of-nginx-configure)

## 我的`nginx.conf`
```bat
# [Leo]=>Nginx配置文件nginx.conf中文详解：http://www.cnblogs.com/sunxucool/p/3225818.html
# [Leo]=>Nginx 配置从零开始：http://www.open-open.com/lib/view/open1419826381531.html
# [Leo]=>Nginx配置杂记：https://wenjs.me/p/note-of-nginx-configure
#user  nobody;
# [Leo]=>worker processes 启动个数
worker_processes  1;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;

# nginx工作模式
events {
    # [Leo]=>最大并发数
    worker_connections  1024;
}

# http设置
http {
    # [Leo]=>引入mime.types文件所声明的文件扩展名与文件类型映射
    include       mime.types;
    # [Leo]=>默认使用application/octet-stream
    default_type  application/octet-stream;

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    # [Leo]=>开启高效文件传输模式
    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;

    # 主机设置
    server {
        # [Leo]=>监听localhost:80
        listen       80;
        server_name  localhost;

        # [Leo]=>设置网页的默认编码格式。 
        #charset koi8-r;
        #charset utf-8;

        # [Leo]=>指定此虚拟主机的访问日志存放路径，最后的main用于指定访问日志的输出格式
        #access_log  logs/host.access.log  main;

        # [Leo]=>表示在这整个server虚拟主机内，全部的root web根目录。注意要和locate {}下面定义的区分开来。
        #root html;

        # [Leo]=>全局定义访问的默认首页地址。注意要和locate {}下面定义的区分开来。 
        #index  index.html index.htm; 

        # [Leo]=>URL匹配,映射目录为“当前目录的html目录”
        location / {
            root   html;
            index  index.html index.htm;
        }

        #error_page  404              /404.html;

        # [Leo]=>出现500、502、503、504错误，则映射到50x.html
        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }


    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}

    ##################################################################

    server
    {
        listen 80;
        server_name m2.jiuxiulvxing.com;
        access_log c:/Users/lxbin/Documents/WWW/9X_WAP_IM/m.jiuxiulvxing.com_access.log;
        location / {
            #root c:/Users/lxbin/Documents/WWW/9X_WAP_IM/;
            index index.html index.htm;

            #proxy_redirect off;
            #proxy_set_header Host $host;
            #proxy_set_header X-Real-IP $remote_addr;
            #proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            #proxy_pass http://127.0.0.1:8080;
        }
    }

}
```