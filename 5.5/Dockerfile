FROM tetraweb/php:5.5

RUN apt-get update \
    && apt-get install -y zlib1g-dev \
      zlib1g-dev \
      libfreetype6-dev \
      libjpeg62-turbo-dev \
      libmcrypt-dev \
      libpng12-dev

RUN docker-php-ext-install -j$(nproc) iconv mcrypt zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# Install composer parallel plugin
RUN composer global require hirak/prestissimo

# Install bower gulp globaly
RUN npm install -g \
        bower \
        gulp \
        gulp-cli \
        grunt \
        grunt-cli \
        webpack \
        webpack-cli \
        coffee-script

# Install gulp grunt localy
RUN npm install \
        gulp \
        grunt

COPY conf.d/* /usr/local/etc/php/conf.d/

CMD ["php", "-a"]
