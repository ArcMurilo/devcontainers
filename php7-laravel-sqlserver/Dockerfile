FROM php:7-alpine

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
    rm composer-setup.php

# instalando libs
RUN apk add build-base && \
    apk add gnupg && \
    apk add libxml2-dev && \
    apk add libzip-dev && \
    apk add unixodbc-dev && \
    apk add git

# instalando ODBC Drive
RUN curl -O https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.8.1.1-1_amd64.apk && \
    curl -O https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/mssql-tools_17.8.1.1-1_amd64.apk && \
    apk add --allow-untrusted msodbcsql17_17.8.1.1-1_amd64.apk && \
    apk add --allow-untrusted mssql-tools_17.8.1.1-1_amd64.apk

# habilitando extensões do php
RUN docker-php-ext-install pdo && \
    docker-php-ext-install xml && \
    docker-php-ext-install soap && \
    docker-php-ext-install zip && \
    pecl install sqlsrv && \
    pecl install pdo_sqlsrv && \
    docker-php-ext-enable sqlsrv && \
    docker-php-ext-enable pdo_sqlsrv