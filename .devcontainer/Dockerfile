FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    pkg-config \
    libxml2-dev \
    libzip-dev \
    libicu-dev \
    libonig-dev \
    unzip \
    curl \
    git \
    sqlite3 \
    libsqlite3-dev \
    && rm -rf /var/lib/apt/lists/*

# Install PHP from source
WORKDIR /usr/src/php
RUN curl -fsSL https://www.php.net/distributions/php-8.2.13.tar.gz | tar xvz \
    && cd php-8.2.13 \
    && ./configure --enable-mbstring --enable-intl --with-zip \
    && make -j$(nproc) \
    && make install \
    && cd .. \
    && rm -rf php-8.2.13

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set up Node.js and npm
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - \
    && apt-get install -y nodejs

# Set work directory
WORKDIR /workspace

CMD ["sleep", "infinity"]
