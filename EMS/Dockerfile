#========================
# Build backend source
#========================
FROM composer as vendor

WORKDIR /var/www/html

COPY . /var/www/html/
RUN composer install  \
    --ignore-platform-reqs \
    --no-dev \
    --no-interaction \
    --no-progress \
    --no-suggest \
    --optimize-autoloader \
    --prefer-dist

##========================
## Build frontend assets
##========================
#FROM node:10-alpine as frontend
#
#RUN mkdir -p /var/www/html/public/frontend
#
#COPY package.json package-lock.json webpack.mix.js /var/www/html/
#COPY resources /var/www/html/resources
#WORKDIR /var/www/html
#
#RUN yarn install
#RUN npm run production

#========================
# Build app image
#========================
FROM oanhnn/php:7.2-laravel

WORKDIR /var/www/html

COPY --from=vendor /var/www/html /var/www/html
#COPY --from=frontend /var/www/html/public /var/www/html/public
