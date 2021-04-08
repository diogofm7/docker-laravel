FROM nginx:alpine

ADD vhost.conf /etc/nginx/conf.d/default.conf

RUN rm -Rf /var/www/html

RUN ln -snf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime && echo America/Sao_Paulo > /etc/timezone