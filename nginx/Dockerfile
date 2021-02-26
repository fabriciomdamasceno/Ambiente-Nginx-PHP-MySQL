FROM nginx:stable-alpine
RUN apk update && apk add bash

RUN rm /etc/nginx/conf.d/default.conf
COPY ./laravel.conf /etc/nginx/conf.d
COPY ./php.conf /etc/nginx/conf.d
