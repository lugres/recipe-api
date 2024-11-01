FROM nginxinc/nginx-unprivileged:1-alpine
LABEL maintainer="lugres.com"

COPY ./nginx/* /etc/nginx/
COPY ./run.sh /run.sh

ENV APP_HOST=app
ENV APP_PORT=9000

USER root

RUN apk add --no-cache openssl bash
RUN mkdir -p /vol/static && \
    chmod 755 /vol/static && \
    touch /etc/nginx/conf.d/default.conf && \
    chown nginx:nginx /etc/nginx/conf.d/default.conf && \
    chmod +x /run.sh && \
    mkdir -p /vol/proxy && \
    chown nginx:nginx /vol/proxy

VOLUME /vol/static
VOLUME /vol/www
VOLUME /vol/proxy

USER nginx

CMD [ "/run.sh" ]