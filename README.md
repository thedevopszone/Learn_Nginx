# Learn Nginx


## Nginx as Reverse Proxy for Podman/Docker

Simplest Config: /etc/nginx/nginx.conf
```
events {}
http {
    server {
        listen 80;
        server_name jenkins99.home.local;
        location /
                {
                    proxy_pass http://127.0.0.1:8080;
                }

    }

}
```

Or in /etc/nginx/conf.d/jenkins99.home.local.conf
```
server {
    listen 80;
    server_name jenkins99.home.local;
    location /
            {
                proxy_pass http://127.0.0.1:8080;
            }

}
```
