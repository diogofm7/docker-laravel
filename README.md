## Build Nginx

`` docker build -f NGINX/Dockerfile -t user/name_image:tag .``

## Build PHP

``  docker build --build-arg PHP_VERSION=8 -f PHP/Dockerfile -t user/name_image:tag .``

## Build PHP WORKER

`` docker build --build-arg PHP_VERSION=8 -f PHP-WORKER/Dockerfile -t user/name_image:tag .``
