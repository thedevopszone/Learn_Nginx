# Learn Nginx


## Nginx as Reverse Proxy for Podman/Docker


# Simple Example

Simplest Config: /etc/nginx/nginx.conf
```
events {}
http {
    server {
        listen 80;
        server_name test.home54.de;
        location /
                {
                    proxy_pass http://127.0.0.1:8080;
                }

    }

}
```



# Example With TLS

vi /etc/nginx/conf.d/default.conf
```
server {
    listen       80;
    listen  [::]:80;
    server_name  localhost;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    error_page   500 502 503 504  /50x.html;

    location = /50x.html {
        root   /usr/share/nginx/html;
    }

}

```


vi /etc/nginx/conf.d/jenkins.conf
```
server {
  listen 80;
  server_name xxx.de;

  location / {
    proxy_pass http://172.xxxx:8080;
  }

}

 
server {
  listen 443 ssl;
  server_name xxx.de;

  ssl_certificate /etc/nginx/ssl/xxx.crt;
  ssl_certificate_key /etc/nginx/ssl/xxx.key;

  location / {
    proxy_pass http://172.xxxx:8080;
  }

}
```





# From Cloud Guru

```
server {
    listen 80 default_server;
    server_name _;
    return 301 https://$host$request_uri;
}


server {
    listen 443 ssl;
    server_name _;

    ssl_certificate /etc/nginx/ssl/public.pem;
    ssl_certificate_key /etc/nginx/ssl/private.key;

    location / {
        proxy_pass http://localhost:8080;
    }

}
```






