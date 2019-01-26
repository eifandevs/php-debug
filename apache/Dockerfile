# php7以上でないとxdebugがインストールできない
FROM php:7.2-apache

# htaccess有効化
RUN apache2ctl -M && /usr/sbin/a2enmod rewrite

# setup
RUN apt-get update && \
    sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main" > /etc/apt/sources.list.d/pgdg.list' && \
    apt-get install -y wget ca-certificates gnupg && \
    curl -O -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc && \              
    apt-key add ACCC4CF8.asc && \
    apt-get update && \
    apt-get install -y postgresql-client-10 nano libicu-dev libpq-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev libmcrypt-dev && \
    docker-php-ext-install pdo pdo_pgsql intl mbstring && \
    pecl install xdebug

WORKDIR /var/www

# プロキシ設定
# ARG proxy_user="xxxxxx"
# ARG proxy_password="xxxxxx"
# ARG proxy_host="xxxx:8080"
# ARG no_proxy="xxxx,xxxx,xxxx"

# ENV HTTP_PROXY_USER ${proxy_user}
# ENV NO_PROXY ${no_proxy}
# ENV HTTP_PROXY_PASS ${proxy_password}
# ENV HTTP_PROXY http://${proxy_user}:${proxy_password}@${proxy_host}
# ENV HTTPS_PROXY http://${proxy_user}:${proxy_password}@${proxy_host}
# ENV http_proxy http://${proxy_user}:${proxy_password}@${proxy_host}
# ENV https_proxy http://${proxy_user}:${proxy_password}@${proxy_host}
# ENV proxy http://${proxy_user}:${proxy_password}@${proxy_host}

# RUN echo "Acquire::http::proxy \"http://${proxy_user}:${proxy_password}@${proxy_host}\";" >> /etc/apt/apt.conf \
#     && echo "Acquire::https::proxy \"http://${proxy_user}:${proxy_password}@${proxy_host}\";" >> /etc/apt/apt.conf