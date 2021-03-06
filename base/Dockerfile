FROM php:7.4-alpine
MAINTAINER Tobias Nyholm <tobias.nyholm@gmail.com>

ENV COMPOSER_HOME /composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV PATH /composer/vendor/bin:$PATH

RUN set -e && \
    apk add --no-cache --update --progress git icu gmp && \
    apk add --no-cache --update --progress --virtual build-deps icu-dev gmp-dev && \
    docker-php-ext-install -j$(nproc) pcntl intl bcmath gmp && \
    echo "memory_limit=-1" > $PHP_INI_DIR/conf.d/99_memory-limit.ini && \
    apk del build-deps && \
    rm -rf /var/cache/apk/* /var/tmp/* /tmp/*

COPY --from=composer:2.0 /usr/bin/composer /usr/local/bin/composer

VOLUME ["/app"]
WORKDIR /app

ENTRYPOINT ["roave-backward-compatibility-check"]
