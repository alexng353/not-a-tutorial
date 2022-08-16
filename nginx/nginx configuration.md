## File Server
```nginx
server {
	listen 80;
    server_name YOUR.DOMAIN;
    return 301 https://$server_name$request_uri;
}
    
server {
    listen 443 ssl http2;
    
	server_name YOUR.DOMAIN;
    
	ssl_certificate /root/.acme.sh/YOUR.DOMAIN/fullchain.cer;
	ssl_certificate_key /root/.acme.sh/YOUR.DOMAIN/YOUR.DOMAIN.key;
    
	root /root/YOUR.DOMAIN;
    
	index index.html;
}
```

## Reverse Proxy
```nginx
server {
	listen 80;
    server_name YOUR.DOMAIN;
    return 301 https://$server_name$request_uri;
}
    
server {
    listen 443 ssl http2;
    
	server_name YOUR.DOMAIN;
    
	ssl_certificate /root/.acme.sh/YOUR.DOMAIN/fullchain.cer;
	ssl_certificate_key /root/.acme.sh/YOUR.DOMAIN/YOUR.DOMAIN.key;
    
	location / {
		proxy_pass http://localhost:PORT;
	}
}
```