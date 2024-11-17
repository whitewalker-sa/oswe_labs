# Use the official PHP image with Apache
FROM php:7.4-apache

# Copy application files to the web server directory
COPY ./www /var/www/html

# Set the working directory
WORKDIR /var/www/html

# Enable necessary Apache modules (e.g., mod_rewrite)
RUN a2enmod rewrite

# Install any required PHP extensions (example: mysqli)
RUN docker-php-ext-install mysqli
RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev && docker-php-ext-configure gd --with-freetype --with-jpeg && docker-php-ext-install gd
RUN echo "session.save_path = /var/lib/php/sessions" >> /usr/local/etc/php/conf.d/custom.ini


# Expose port 80
EXPOSE 80

# Start the Apache server
CMD ["apache2-foreground"]
