FROM nginx:latest

RUN usermod -u 1001 nginx && groupmod -g 1001 nginx
WORKDIR /app
COPY ./config/default.conf /etc/nginx/conf.d/default.conf

EXPOSE 8000
