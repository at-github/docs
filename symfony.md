# Symfony

## Migrations

### A way to rollback

`symfony console doctrine:migrations:diff`

Then :

`symfony console doctrine:migrations:execute --up 'DoctrineMigrations\<migrationidprovidedbythepreviouscommand>'`

## Some commands to order

### Database

- `symfony run psql`
- `symfony console make:entity EntityName`
- `symfony console make:user User`
- `symfony console make:migration`
- `symfony console doctrine:migrations:migrate`


### Debug & env

- `symfony var:export --multiline`
- `symfony console debug:router`
- `symfony console debug:autowiring hasher`
- `symfony server:status`
- `symfony server:log`
- `symfony console secrets:set AKISMET_KEY`

### EasyAdmin

- `symfony console make:admin:dashboard`
- `symfony console make:admin:crud`
- `symfony console make:auth`


### Test

- `symfony console make:test TestCase SpamCheckerTest`
- `symfony php bin/phpunit`

```shell
symfony console doctrine:fixtures:load --env=test
symfony php bin/phpunit tests/Controller/ConferenceControllerTest.php
```

`symfony composer req "dama/doctrine-test-bundle:^6" --dev`

```shell
symfony console make:test WebTestCase Controller\\ConferenceController
symfony console make:test PantherTestCase Controller\\ConferenceController
```

```shell
symfony server:stop
APP_ENV=test symfony server:start -d
```

```
symfony console doctrine:database:create --env=test
symfony console doctrine:migrations:migrate -n --env=test
```

```
symfony composer req orm-fixtures --dev
symfony console doctrine:fixtures:load --env=test
```

### Bus

**Show the message count for one or more transports**

`symfony console messenger:stats`

- `symfony console make:subscriber TwigEventSubscriber`
- `symfony composer req doctrine-messenger`
- `symfony console messenger:consume async -vv`
- `symfony run -d --watch=config,src,templates,vendor symfony console messenger:consume async -vv`
- `symfony console messenger:failed:show`
- `symfony console messenger:failed:retry`
