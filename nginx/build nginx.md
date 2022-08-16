https://www.alibabacloud.com/blog/how-to-build-nginx-from-source-on-ubuntu-20-04-lts_597793
http://nginx.org/en/docs/http/ngx_http_realip_module.html
http://nginx.org/en/docs/configure.html

```bash
sudo apt-get update 

sudo apt-get install build-essential libpcre3 libpcre3-dev zlib1g zlib1g-dev libssl-dev libgd-dev libxml2 libxml2-dev uuid-dev

# sometimes you might need to exec bash too 

# REMEMBER change this to the latest version of NGINX (as of writing, latest version is 1.23.0)
wget  http://nginx.org/download/nginx-1.23.0.tar.gz 

# To extract download tar.gz 
# REMEMBER change this one too
tar -zxvf nginx-1.23.0.tar.gz

# THIS ONE TOO
cd nginx-1.23.0

# This command configures the make thing (c is weird asf)
./configure --prefix=/var/www/html --sbin-path=/usr/sbin/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --with-pcre  --lock-path=/var/lock/nginx.lock --pid-path=/var/run/nginx.pid --with-http_ssl_module --with-http_image_filter_module=dynamic --modules-path=/etc/nginx/modules --with-http_v2_module --with-stream=dynamic --with-http_addition_module --with-http_mp4_module --with-http_realip_module


make

make install

# Check if nginx works
nginx -V




```