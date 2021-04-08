ARG PHP_VERSION=7.4

FROM diogofm7/php-fpm:${PHP_VERSION}-alpine

RUN apk update && apk add --no-cache supervisor

WORKDIR /etc/supervisor/conf.d/

COPY supervisord.conf /etc/supervisord.conf

COPY supervisord.d /etc/supervisord.d

RUN ln -snf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime && echo America/Sao_Paulo > /etc/timezone

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]