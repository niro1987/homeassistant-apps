# WordPress

This app runs the official WordPress Apache image. It requires a running MariaDB
app and a database/user with permission to create tables.

## Database

Set the database host, name, username, and password in the app's Configuration
tab. The default host is `core-mariadb`; change it if your MariaDB app uses a
different hostname. Create the database and grant the configured user access
before starting WordPress.

## Edit `wp-config.php`

The app creates `wp-config.php` on its first start and stores it in the app's
configuration folder. In Samba, SSH, or a file editor app, open
`app_configs/local_wordpress/wp-config.php`. Adjust the configuration there,
then restart WordPress for changes to take effect. On startup, the local file
is copied into the WordPress site.

Database values configured in the app are read from environment variables by
the default config file. You can also edit the PHP file directly to add custom
WordPress settings.

## Website files

WordPress core and site files are stored in the app's persistent data folder.
The web interface is available on port `8080` by default. Change the host port
in the app's Network settings if it conflicts with another service.
