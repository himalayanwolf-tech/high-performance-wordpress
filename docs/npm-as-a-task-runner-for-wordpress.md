# NPM for task running

```sh
{
  "name": "himalayanwolf.in",
  "version": "0.1.0",
  "description": "WordPress Website",
  "main": "index.js",
  "scripts": {
    "start-without-nginx": "php -S localhost:8000",
    "open": "open http://himalayanwolf.test",
    "nginx-test": "sudo nginx -t",
    "nginx-reload": "brew services restart nginx",
    "php-fpm-reload": "brew services restart php",
    "mysql-restart": "brew services restart mysql",
    "mysql-restart-alternate": "sudo mysql.server start",
    "download-phpmyadmin": "cd ..; wget https://files.phpmyadmin.net/phpMyAdmin/5.0.2/phpMyAdmin-5.0.2-all-languages.zip; unzip phpMyAdmin-5.0.2-all-languages.zip;mv phpMyAdmin-5.0.2-all-languages phpMyAdmin",
    "link-phpmyadmin": "ln -s ../phpMyAdmin/ phpmyadmin",
    "open-phpmyadmin": "open http://himalayanwolf.test/phpmyadmin",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Vijaya Krisha A",
  "license": "ISC"
}


```

# install.sh

```sh
#!/bin/bash

# update nginx user
# update php-fpm user


# all nginx to use storage for caching 
sudo chown -R ubuntu: /var/lib/nginx

```

# Setup backup

```sh
#!/bin/bash

# update nginx user
# update php-fpm user


# all nginx to use storage for caching 
sudo chown -R ubuntu: /var/lib/nginx
```

# Cron Jobs

```sh
git clone https://github.com/himalayanwolf.in/www
cd jobs
chmod +x setup.sh
./setup.sh

```

## setup cron

```sh
crontab -e
```

```sh
@daily /home/ubuntu/himalayanwolf/himalayanwolf.in/jobs/daily-backup.sh
```
