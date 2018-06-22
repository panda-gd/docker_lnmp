FROM daocloud.io/library/php:7.0.13-fpm

RUN sed -i "s/archive.ubuntu./mirrors.aliyun./g" /etc/apt/sources.list 
RUN sed -i "s/deb.debian.org/mirrors.aliyun.com/g" /etc/apt/sources.list 

RUN apt-get clean -y
RUN apt update
RUN apt upgrade -y
RUN apt-get install -y \
    libpng-dev \
    libpq-dev \
    g++ \
    libicu-dev \
    libxml2-dev \
    htop \
    git \
    vim \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    zlib1g-dev \
    librabbitmq-dev
    
RUN apt install -y curl
RUN apt install -y libcurl3
RUN apt install -y libcurl3-dev

RUN docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install soap \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install opcache \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install pcntl \
    && docker-php-ext-install posix

#RUN  docker-php-ext-install mcrypt

ADD php.ini /usr/local/etc/php/