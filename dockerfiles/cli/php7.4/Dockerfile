FROM php:7.4-cli

RUN \
    curl -sfL http://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
    chmod +x /usr/bin/composer && \
    docker-php-source extract && \
    mkdir /usr/src/php/ext/swow && \
    curl -sfL https://github.com/swow/swow/archive/6bb4ce0dde3df6b308a9c33153e3f2aae55c7771.tar.gz -o swow.tar.gz && \
    tar xfz swow.tar.gz --strip-components=2 -C /usr/src/php/ext/swow swow-6bb4ce0dde3df6b308a9c33153e3f2aae55c7771/ext && \
    docker-php-ext-configure swow && \
    docker-php-ext-install -j$(nproc) swow && \
    rm -f swow.tar.gz $HOME/.composer/*-old.phar && \
    docker-php-source delete
