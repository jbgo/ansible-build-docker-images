FROM ubuntu:latest

RUN apt-get install -y nginx
ADD nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /var/www/site
ADD index.html /var/www/site/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
