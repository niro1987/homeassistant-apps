FROM wordpress:php8.3-apache

COPY rootfs /

RUN chmod 0755 /usr/local/bin/wp-app-entrypoint

ENTRYPOINT ["/usr/local/bin/wp-app-entrypoint"]
CMD ["apache2-foreground"]
