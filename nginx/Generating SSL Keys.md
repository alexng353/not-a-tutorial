## Generating SSL Keys

### Install acme.sh
- This first step installs a utility for getting SSL keys from zerossl (and other places)
```bash
curl https://get.acme.sh | sh -s email=my@example.com
```
### Generate a key pair

- The CF_Key should be the Global API Key from https://dash.cloudflare.com/profile/api-tokens 
- The CF_Email should be your cloudflare email (the one your account is linked to)
- your.domain is generic and if you don't want a key that can access every subdomain, remove `-d '*.your.domain'`

```bash
#set environment variables
export CF_Key="key"
export CF_Email="alexng353@gmail.com"
	
# run acme.sh script
acme.sh --issue --dns dns_cf -d your.domain -d '*.your.domain'
```

- your.domain here is also generic
- 
Nginx Config
```nginx
ssl_certificate /root/.acme.sh/your.domain/fullchain.cer
ssl_certificate_key /root/.acme.sh/your.domain/your.domain.key
```