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


## From Cloud Guru

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






