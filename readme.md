### if do not have it please install the followings

sudo apt-get install php-xml
sudo apt-get install php-gd
sudo apt-get install php-intl

### create drupal project

composer create-project drupal/recommended-project drupal

### copy content from drupal folder to root and remove drupal

cp -a ./drupal/. ./
sudo rm -rf ./drupal/

### copy and pest the following code to ./web/sites/default/default.settings.php

```
$databases['default']['default'] = array (
  'database' => 'drupalDB',
  'username' => 'root',
  'password' => 'pass',
  'prefix' => '',
  'host' => 'drupaldb',
  'port' => '3306',
  'isolation_level' => '',
  'namespace' => 'Drupal\\mysql\\Driver\\Database\\mysql',
  'driver' => 'mysql',
  'autoload' => 'core/modules/mysql/src/Driver/Database/mysql/',
);
```

### copy default.settings.php to settings.php

cp ./web/sites/default/default.settings.php ./web/sites/default/settings.php

### build the container

docker compose up -d

composer require --dev drush/drush

wget -O drush.phar https://github.com/drush-ops/drush-launcher/releases/latest/download/drush.phar

chmod +x drush.phar

sudo mv drush.phar /usr/local/bin/drush

export DRUSH_LAUNCHER_FALLBACK=/path/to/drush
