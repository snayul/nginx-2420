1. install nginx with ``` sudo pacman -S nginx```

2. start nginx with ``` sudo systemctl start nginx```

3. check status with ``` sudo systemctl enable nginx```

4. check status with ``` sudo systemctl status nginx``` to make sure its enabled

5. install vim with ``` sudo pacman -S vim```

6. create directory /web/html/nginx-2420

7. create directory ``` mkdir  /etc/nginx/sites-available 
                        mkdir  /etc/nginx/sites-enabled ```
8. create server block config file in /sites-available/example.conf
    ``` server {
    listen 443 ssl;
    listen [::]:443 ssl;
    http2 on;

    ...
}
```
9. I changed my /etc/nginx/nginx.conf file to the one provided by wiki.archlinux.org/title/Nginx, it uses include /etc/nginx/sites-enabled/* in the http block for easy site management.

``` user http;
worker_processes auto;
worker_cpu_affinity auto;

events {
    multi_accept on;
    worker_connections 1024;
}

http {
    charset utf-8;
    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    server_tokens off;
    log_not_found off;
    types_hash_max_size 4096;
    client_max_body_size 16M;

    # MIME
    include mime.types;
    default_type application/octet-stream;

    # logging
    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log warn;

    # load configs
    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
}```

10. 
enable the site by creating a symlink: 
```
ln -s /etc/nginx/sites-available/example.conf /etc/nginx/sites-enabled/example.conf ```
