# WP CLI

## Fresh install wordpress

```bash
wp core download
wp config create --dbname=dbname --dbuser=dbuser --dbhost=localhost --dbprefix=wp_prefix_ --dbpass="pass"
wp core install --url=do.main --title='title' --admin_user=pseudo --admin_email=e@ma.il
```
