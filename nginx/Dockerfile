FROM nginx:stable-alpine
RUN apk update && apk add bash

RUN rm /etc/nginx/conf.d/default.conf
COPY ./app.conf /etc/nginx/conf.d
COPY ./app2.conf /etc/nginx/conf.d
