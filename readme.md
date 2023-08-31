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

### installing drupal site

- go to: http://localhost:8082/
- go through the installation process

### Error: File system: In Verify requirements section (you may encounter)

- Problem: The directory sites/default/files does not exist. An automated attempt to create this directory failed, possibly due to a permissions problem.

- Solution: Reloading the page fixs the problem and create the folder. If it does not fix the problem, please check the permission of the directory

### Error: Settings file: In Verify requirements section

- Problem: The Settings file does not exist.

- Solution:

```
cp ./web/sites/default/default.settings.php ./web/sites/default/settings.php
```

- When it is get created, reload the page

### configur database with the following info

- You may need to click "Advanced options" to see all the fields

```

  database: drupalDB
  username: root
  password: pass
  host: drupaldb
  port: 3306

```

Now you would be able to see your new drupal site.

### copy example.gitignore to .gitignore (optional)

```
cp ./example.gitignore ./.gitignore
```

## **_CAUTION:_**

- It will delete any database named "drupalDB" during installation if it's already existed.
- If ports: "3306", "80", "3308", "9082", "8082" are in use by any other services during installation, container related to conflicting port may not install or run.
