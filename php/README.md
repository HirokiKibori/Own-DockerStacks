# PHP
A XAMPP-like docker-compose.

Started with the tutorial
"[docker-php-development-environment](https://www.sitepoint.com/docker-php-development-environment/)"
and added phpmyadmin later. Files in directory *./app/public* are able to request from localhost.

**Only for development! Don't run this in a productive setup without editing before.**

Run command in root-directory:
```bash
docker-compose up
```

Open *nginx* with [localhost](http://localhost/)  
Open *index.php* with [127.0.0.1](http://127.0.0.1/)

## Services
- **nginx (:80)**: nginx:latest  
-> ./nginx.conf
- **php**: PHP.dockerfile (php:fpm)   
-> ./app/*
- **mysql**: mariadb:latest ('--character-set-server=utf8mb4' '--collation-server=utf8mb4_unicode_ci')  
-> ./mysqldata/data | ./mysqldata/logs
- **phpmyadmin (:8080)**: phpmyadmin:latest  
-> ./phpmyadmin_theme

## Files 
- **.env**: global configuration for ports and database
- **nginx.conf**: configuration for nginx
- **PHP.dockerfile**: builds a docker-image for php with pdo, pdo_mysql and xdebug, while docker-compose is running the first time