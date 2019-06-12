# docker-compose-wp

This repository contains docker-compose files for Wordpress.
I have tuned parameters for a server which has CPU 2 core and Memory 2 GB.

## Requirements

- Docker
- docker-compose

## Features

- Wordpress
    - php-fpm 7.3
- Nginx
    - Enabled http2
    - Enabled client-side cache (html/js/css/png/jpeg/gif/webp)
    - Enabled fastcgi cache (wait up to 10 minutes if the change is not reflected)
    - Redirect http to https
        - Disabled HSTS for developments
    - Redirect PNG and JPEG files to WebP for EWWW Optimizer
- MySQL 5.7

## Usage

1. change database password on docker-compose file (temporary password is `CHANGE_ME`)
2. generate certifications to `nginx/etc/nginx/ssl`
3. `docker-compose up`

## About certifications

### Generate certifications for test

```sh
openssl genrsa -out nginx/etc/nginx/ssl/server.key 2048 \
 && openssl req -new -sha256 -key nginx/etc/nginx/ssl/server.key -subj "/C=JP/CN=localhost" -out nginx/etc/nginx/ssl/server.csr \
 && openssl x509 -in nginx/etc/nginx/ssl/server.csr -days 3650 -req -signkey nginx/etc/nginx/ssl/server.key > nginx/etc/nginx/ssl/server.crt
```

### Generate certifications with certbot

TODO
