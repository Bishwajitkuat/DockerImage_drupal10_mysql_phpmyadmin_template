### if you do not have it please install the followings

```
sudo apt-get install php-xml
sudo apt-get install php-gd
sudo apt-get install php-intl
```

### create a project folder and cd into the project folder

### create drupal project with latest drupal

```
composer create-project drupal/recommended-project drupal
```

### copy content from drupal folder to root and remove drupal

```
cp -a ./drupal/. ./
sudo rm -rf ./drupal/
```

### build the container

```
docker compose up -d
```

- check all the containers are up and running

### Installing drupal site

- go to: http://localhost:8082/
- go through the installation process
- \*\*\*In verify requirements, you may encounter an error: sites/default/files folder can not be created due to permission problem. Reloading the page fix the problem and create the folder. If it does not fix the problem, please check the permission of the directory\*\*\*.

### Error: Settings file:

- solution: copy default.settings.php to settings.php

```
cp ./web/sites/default/default.settings.php ./web/sites/default/settings.php
```

- when it is get created reload the page

### configur database with the following info

```

  database: drupalDB
  username: root
  password: pass
  host: drupaldb
  port: 3306

```

composer require --dev drush/drush

wget -O drush.phar https://github.com/drush-ops/drush-launcher/releases/latest/download/drush.phar

chmod +x drush.phar

sudo mv drush.phar /usr/local/bin/drush

export DRUSH_LAUNCHER_FALLBACK=/path/to/drush
