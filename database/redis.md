# STUPID FRICKING REDIS REDIS REDIS

## How to start redis
sudo service redis-server start

(if errors mostly its cuz its already running on 6379 so just sudo kill -9 \`sudo lsof -t -i:6379`

## Redis cli
redis-cli

## Set persistence interval
save 60 1000
(saves every 60 seconds for 1000+ key updates)

REDIS RUNS ON PORT 6379

# Config
```conf
bind TAILSCALE_IP 127.0.0.1
```

```bash
redis-cli


127.0.0.1:6379> config set protected-mode "no"
```