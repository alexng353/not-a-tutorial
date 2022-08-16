## Example static file server
[[nginx configuration]]
location: /etc/nginx/conf.d/www.edubeyond.dev.conf
```nginx
server {
        listen 80 default_server;
        server_name www.edubeyond.dev;

        location / {
                root /data/www/;
                index index.html;
        }
}
```

[[Generating SSL Keys]]

## Reverse Proxy
```
i forgor
```