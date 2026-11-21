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
configuration folder. The folder is separate from Home Assistant's `/config`
directory and is not under `/config/www`. Use Samba or SSH to open
`app_configs/<app-id>/wp-config.php`; for example, the app ID in Supervisor
logs may appear as `16aa57ea_wordpress`. Adjust the configuration there, then
restart WordPress for changes to take effect. On startup, the local file is
copied into the WordPress site.

WordPress core and site files are stored separately in the app's private
persistent data, not in Home Assistant's `/config` folder.

Database values configured in the app are read from environment variables by
the default config file. You can also edit the PHP file directly to add custom
WordPress settings.

## Open WordPress in Home Assistant

Ingress is enabled, so use **Open Web UI** on the app page or enable WordPress
in the Home Assistant sidebar. WordPress URLs use Home Assistant's ingress
path, including admin and login redirects. The direct host port `8080` remains
available for external access.

If you customize `wp-config.php`, keep its `WORDPRESS_CONFIG_EXTRA` evaluation
in place and avoid hard-coding `WP_HOME` or `WP_SITEURL`; those constants are
set dynamically for ingress requests.

## Website files

WordPress core and site files are stored in the app's persistent data folder.
The direct web interface is available on port `8080` by default. Change the
host port in the app's Network settings if it conflicts with another service.
