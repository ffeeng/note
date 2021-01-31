## mac安装nginx
1. 安装brew命令

`ruby -e ``"$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

- 若出现报错信息

`Failed to connect to raw.githubusercontent.com port 443: Connection refused`

- 需要修改/etc/hosts文件，添加

`199.232.28.133 raw.githubusercontent.com`

- 重新执行，安装brew命令

- 若提示指令过期，执行
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`



2. 简单安装方法：`/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"`

3. 安装nginx

`brew install nginx`

4. 启动nginx

`sudo nginx`

5. 常用命令

```
nginx -s 指令
```

- `stop` — fast shutdown
- `quit` — graceful shutdown
- `reload` — reloading the configuration file
- `reopen` — reopening the log files
6. 配置文件路径

`/usr/local/etc/nginx/nginx.conf`

7. 示例

```nginx
server {
    listen       8080;
    server_name  localhost;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location /app/ {
        proxy_pass  http://ip:port/app/;
    }

    location /console/ {
        proxy_pass  http://ip:port/console/;
    }

    location /v2/ {
        proxy_set_header  Host  $host;
        proxy_set_header   X-Real-IP $remote_addr;  
        proxy_set_header   x-forwarded-for $proxy_add_x_forwarded_for;
        proxy_pass  http://127.0.0.1:3000/v2/;
    }

    location / {
        proxy_pass  http://ip:port/;
    }
        # 开启_ 下划线头
    underscores_in_headers on;

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
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
```

## linux上nginx 常用命令

```shell
nginx -t
nginx -s reload

systemctl stop nginx
systemctl restart nginx
systemctl status nginx
```

​    

### 参考
- [nginx指令](https://nginx.org/en/docs/dirindex.html)
- [nginx内置变量](https://nginx.org/en/docs/varindex.html)

