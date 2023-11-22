# Utilisation de l'image PHP officielle avec PHP 8.2
FROM php:8.2-fpm

# Installation des dépendances
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libpq-dev \
    && docker-php-ext-install \
    pdo_pgsql

# Copie des fichiers du projet
COPY . /usr/src/app

# Définition du répertoire de travail
WORKDIR /usr/src/app

# Installation des dépendances de l'application via Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN composer install

# Exposition du port 9000
EXPOSE 9000

# Commande pour démarrer le serveur PHP-FPM
CMD ["php-fpm"]
