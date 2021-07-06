FROM laravelsail/php74-composer

WORKDIR /workspace

RUN apt-get update \
    && curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh \
    && bash nodesource_setup.sh \
    && apt install -y nodejs \
    && rm nodesource_setup.sh