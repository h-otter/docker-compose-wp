# docker-compose-wp

docker-compose files for wordpress.

## Features

- Wordpress
- php-fpm 7.3
- Nginx
- MySQL 5.7

## About certifications

### Generate certifications for test

```sh
openssl genrsa -out nginx/etc/nginx/ssl/server.key 2048 \
 && openssl req -new -sha256 -key nginx/etc/nginx/ssl/server.key -subj "/C=JP/CN=localhost" -out nginx/etc/nginx/ssl/server.csr \
 && openssl x509 -in nginx/etc/nginx/ssl/server.csr -days 3650 -req -signkey nginx/etc/nginx/ssl/server.key > nginx/etc/nginx/ssl/server.crt
```
