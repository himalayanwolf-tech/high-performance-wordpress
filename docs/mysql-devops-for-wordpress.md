# Setup

## Installing MySQL

```sh
brew install mysql
brew services start mysql
mysql_secure_installation
# give password for root as <password>, note down somewhere for further reference
````

## Connecting MySQL with WordPress
- Goto https://db1.cureskin.com/phpmyadmin
- Select Database
- Click on Export -> click on Go

```sh
cd ~/Downloads
mysql -u root -p
> create database himalayanwolf_public
> use himalayanwolf_public
> source himalayanwolf_public.sql

```


## in Mac
- Removing existing php and installing new php worked well https://medium.com/@romaninsh/install-php-7-2-xdebug-on-macos-high-sierra-with-homebrew-july-2018-d7968fe7e8b8


```sh
brew install nginx  
launchctl load /usr/local/cellar/nginx/1.17.0/homebrew.mxcl.nginx.plist 

launchctl load -w  ~/Library/LaunchAgents/homebrew.mxcl.php*.plist
```

## Stop
```sh
launchctl unload -w ~/Library/LaunchAgents/homebrew.mxcl.php*.plist  

## check php fpm process running
sudo lsof -i tcp:9000 

sudo tail -f /usr/local/var/log/nginx/error.log

```

- Add configs in -> `/usr/local/etc/nginx/servers/`
- Default config -> `/usr/local/etc/nginx/nginx.conf`
- Logs will be in -> `/usr/local/var/log/nginx/`
- Default webroot is -> `/usr/local/var/www/`
- Default listen address -> http://localhost:8080

## PHPMyAdmin

- https://www.phpmyadmin.net/downloads/
https://medium.com/@dhirendrapratap/inshorts-how-to-install-nginx-with-php-fpm-in-macos-using-brew-484cb4fc0266
- unzip file

```sh
ln -s ~/himalayanwolf/phpmyadmin /usr/local/var/www/
```

- https://www.javatpoint.com/installing-nginx-on-mac

## php & php fpm
```sh
brew services start php@7.3

nano /usr/local/etc/php/7.3/php-fpm.d/www.conf

sudo tail -f /usr/local/var/log/php-fpm.log
```
- https://medium.com/@dhirendrapratap/inshorts-how-to-install-nginx-with-php-fpm-in-macos-using-brew-484cb4fc0266
- https://gist.github.com/jpalala/c293ed671fc1f86805d9b09f7f6989ff
- http://www.leeladharan.com/installing-php-7-with-nginx-on-mac-os-x

## NGINX OpenSSL Error in Mac

```sh
brew update && brew upgrade
brew uninstall openssl
brew install https://github.com/tebelorg/Tump/releases/download/v1.0.0/openssl.rb
```
- https://stackoverflow.com/questions/44125147/dyld-library-not-loaded-usr-local-opt-openssl-lib-libcrypto-1-0-0-dylib
