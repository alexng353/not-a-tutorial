## File Server
```nginx
server {
	listen 80;
    server_name www.edubeyond.dev;
    return 301 https://$server_name$request_uri;
}
    
server {
    listen 443 ssl http2;
    
	server_name www.edubeyond.dev;
    
	ssl_certificate /root/.acme.sh/edubeyond.dev/fullchain.cer;
	ssl_certificate_key /root/.acme.sh/edubeyond.dev/edubeyond.dev.key;
    
	root /root/www.edubeyond.dev;
    
	index index.html;
}
```

## Reverse Proxy
```nginx
server {
	listen 80;
    server_name www.edubeyond.dev;
    return 301 https://$server_name$request_uri;
}
    
server {
    listen 443 ssl http2;
    
	server_name www.edubeyond.dev;
    
	ssl_certificate /root/.acme.sh/edubeyond.dev/fullchain.cer;
	ssl_certificate_key /root/.acme.sh/edubeyond.dev/edubeyond.dev.key;
    
	root /root/www.edubeyond.dev;
    
	location / {
		proxy_pass http://localhost:port;
	}
}
```