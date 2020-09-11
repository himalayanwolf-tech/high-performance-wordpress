# Wordpress Dev Env

WordPress 5.4.1

## Requirements

- Ubuntu 18.04
- PHP 7.2 with FPM
- NGINX
- MySQL

## Installing Ubuntu Server

username: `ubuntu`

## Installing PHP 7.4.7

```sh
sudo timedatectl set-timezone Asia/Kolkata

sudo apt install nginx -y

sudo apt install php7.2 php7.2-fpm php7.2-mysql php-common php7.2-cli php7.2-common php7.2-json php7.2-opcache php7.2-readline php7.2-mbstring php7.2-xml php7.2-gd php7.2-curl -y


sudo systemctl enable php7.2-fpm
sudo systemctl start php7.2-fpm
sudo systemctl status php7.2-fpm
```

References: [How to Install LEMP Stack (Nginx, MariaDB, PHP7.2) on Ubuntu 18.04 LTS](https://www.linuxbabe.com/ubuntu/install-lemp-stack-nginx-mariadb-php7-2-ubuntu-18-04-lts)

## Setting Up in Test(Production Like) Environment

```shell script
ssh ubuntu@staging-app1.example.com
mkdir himalayanwolf
cd himalayanwolf
git clone https://github.com/himalayanwolf/himalayanwolf.in.git
cd himalayanwolf.in
cp wp-config-sample.php wp-config.php
# update mysql connection details
vim wp-config.php

# update mysql connection details
vim wp-config.php

sudo vim /etc/nginx/nginx.conf
# add include based on your env

```

Open [http://localhost:8000](http://localhost:8000)

## NGINX and PHP-FPM Config

As we are storing code in `/home/ubuntu/himalayanwolf/himalayanwolf.in`
files are owned by user `ubuntu`

so `php-fpm` can read files if it is allowed to access

we can enable the settings using

```sh
sudo nano /etc/php/7.2/fpm/pool.d/www.conf
```

change
```sh
user = ubuntu
group = ubuntu

listen.owner = ubuntu
listen.group = ubuntu
```

then
```sh
sudo systemctl restart php7.2-fpm
```

#### NGINX
```sh
sudo nano /etc/nginx/nginx.conf
```
change
```sh
user ubuntu;
```

save the file and then 
```sh
sudo nginx -t
sudo systemctl restart nginx
```

Visit https://himalayanwolf.in to verify


```sh
sudo chown -R ubuntu: /var/lib/nginx
```

### Permissions
```sh
cd ~/himalayanwolf/himalayanwolf.in; find . -type d -print0|xargs -0 chmod 755; find . -type f -print0|xargs -0 chmod 644; chown ubuntu:ubuntu * -R
```


## Developers Guide

```sh
brew install php
brew install mysql
brew install nginx

sudo nano /etc/hosts
# add below line without #
# 127.0.0.1 himalayanwolf.test

sudo nano /usr/local/etc/nginx/nginx.conf
# search for include and below to that without # 
# include /Users/vijaya/himalayanwolf/www/nginx/development/conf.d/*.conf;

sudo nginx -t
sudo nginx -s reload

sudo chown _mysql /usr/local/var/mysql/*
sudo chmod -R 777 /usr/local/var/mysql/ 
npm run mysql-start-alertnate

## in another tab
mysql_secure_installation
# Password: manjesh123


## nginx error logs
sudo tail -f /usr/local/var/log/nginx/error.log

sudo chown -vhR $USER:admin /usr/local/var/run/nginx
sudo chmod o+x /usr/local/var
sudo chown -vhR nobody:admin /usr/local/var/run/nginx
sudo chmod -R 777 /usr/local/var/run/nginx




```
