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
