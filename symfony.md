# Symfony

## Migrations

### A way to rollback

`symfony console doctrine:migrations:diff`

Then :

`symfony console doctrine:migrations:execute --up 'DoctrineMigrations\<migrationidprovidedbythepreviouscommand>'`
