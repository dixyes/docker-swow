FROM php:7.4-alpine

RUN \
    curl -sfL http://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
    chmod +x /usr/bin/composer && \
    docker-php-source extract && \
    mkdir /usr/src/php/ext/swow && \
    curl -sfL https://github.com/swow/swow/archive/e874691b20cddae2d169e47c05b7b42464f11cc0.tar.gz -o swow.tar.gz && \
    tar xfz swow.tar.gz --strip-components=2 -C /usr/src/php/ext/swow swow-e874691b20cddae2d169e47c05b7b42464f11cc0/ext && \
    docker-php-ext-configure swow && \
    docker-php-ext-install -j$(nproc) swow && \
    rm -f swow.tar.gz $HOME/.composer/*-old.phar && \
    docker-php-source delete
