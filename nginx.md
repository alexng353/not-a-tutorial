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

## Generating SSL Keys

### Install acme.sh
```bash
curl https://get.acme.sh | sh -s email=my@example.com
```
### Generate a keypair
```bash
#set environment variables
export CF_Key="key"
export CF_Email="alexng353@gmail.com"

# run acme.sh script
acme.sh --issue --dns dns_cf -d ayo.icu -d '*.ayo.icu'
```

Nginx Config
```nginx
ssl_certificate /root/.acme.sh/ayo.icu/fullchain.cer
ssl_certificate_key /root/.acme.sh/ayo.icu/ayo.icu.key
```

## Reverse Proxy
```
i forgor
```