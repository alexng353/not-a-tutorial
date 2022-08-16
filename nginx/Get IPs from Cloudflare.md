By default, Nginx doesn't send a connection(client)'s ip to a reverse-proxied web app when connecting through cloudflare, which is what this "tutorial" aims to solve

 [https://developers.cloudflare.com/fundamentals/get-started/reference/http-request-headers/](https://developers.cloudflare.com/fundamentals/get-started/reference/http-request-headers/ "https://developers.cloudflare.com/fundamentals/get-started/reference/http-request-headers/") 
 
 [https://support.cloudflare.com/hc/en-us/articles/200170786](https://support.cloudflare.com/hc/en-us/articles/200170786 "https://support.cloudflare.com/hc/en-us/articles/200170786")
 
 [https://www.cloudflare.com/ips/](https://www.cloudflare.com/ips/ "https://www.cloudflare.com/ips/")

### In order for this to work, you need --with-http_realip_module in your nginx build
Module included by default in [[build nginx]] 

1. Get IP range lists from cloudflare
 [https://www.cloudflare.com/ips/](https://www.cloudflare.com/ips/ "https://www.cloudflare.com/ips/")
2. Add those ranges to nginx config, making sure to change YOUR.DOMAIN and PORT
   **note that the ip ranges DO change from time to time**
These IP ranges were last set 2022-08-16 (y/m/d)
   <details>
   <summary>Example Nginx Config </summary>
   
   ```nginx
   
	server {
	    listen 80;
	    server_name YOUR.DOMAIN;
	    return 301 https://$server_name$request_uri;
	}
	
	server {
	    listen 443 ssl http2;
	
	    server_name YOUR.DOMAIN;
	
		set_real_ip_from 103.21.244.0/22;
		set_real_ip_from 103.22.200.0/22;
		set_real_ip_from 103.31.4.0/22;
		set_real_ip_from 104.16.0.0/13;
		set_real_ip_from 104.24.0.0/14;
		set_real_ip_from 108.162.192.0/18;
		set_real_ip_from 131.0.72.0/22;
		set_real_ip_from 141.101.64.0/18;
		set_real_ip_from 162.158.0.0/15;
		set_real_ip_from 172.64.0.0/13;
		set_real_ip_from 173.245.48.0/20;
		set_real_ip_from 188.114.96.0/20;
		set_real_ip_from 190.93.240.0/20;
		set_real_ip_from 197.234.240.0/22;
		set_real_ip_from 198.41.128.0/17;
	
		set_real_ip_from 2400:cb00::/32;
		set_real_ip_from 2606:4700::/32;
		set_real_ip_from 2803:f800::/32;
		set_real_ip_from 2405:b500::/32;
		set_real_ip_from 2405:8100::/32;
		set_real_ip_from 2a06:98c0::/29;
		set_real_ip_from 2c0f:f248::/32;
	
	
	
		real_ip_header X-Forwarded-For;
		real_ip_recursive on;
	
		ssl_certificate /root/.acme.sh/YOUR.DOMAIN/fullchain.cer;
		ssl_certificate_key /root/.acme.sh/YOUR.DOMAIN/YOUR.DOMAIN.key;
	
		location / {
				proxy_set_header  Host $host;
				proxy_set_header  X-Forwarded-For $remote_addr;
				proxy_set_header  X-Forwarded-Host $remote_addr;
				proxy_pass http://localhost:PORT;
		}
	}
	```
	
</details>

3. `sudo nginx -s reload`

5. Google how to get a header from a request in whichever favourite webserver library you use
   on express, its 
	   
	```js
	app.get("/" (req,res)
		const ip = req.get("X-Forwarded-For")
	)
	```


5. If for some reason yuou don't have  ssl certificates, check out [[Generating SSL Keys]] (if you're on github it should be in the same directory)