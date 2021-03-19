ARG PROJECT_NAME

FROM ${PROJECT_NAME}_app

#USER root

RUN apk update && apk add --no-cache supervisor

WORKDIR /etc/supervisor/conf.d/

COPY supervisord.conf /etc/supervisord.conf

COPY supervisord.d /etc/supervisord.d

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]