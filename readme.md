# Docker Image for Drupal10, MySQL and PhpMyAdmin

## Description

This Image containes three images: Drupal10, MySQL and PhpMyAdmin. The values in the .env file are used during build of the image. If you wish to change the container names and mysql database name, user and password, you can do so in the .env file and init.sql file. This project aims to set up a drupal development environment quickly and efficiently. You must have docker installed and running in order to build this image.

## Technologies:

- Docker
- Drupal10
- MySQL
- PhpMyAdmin
- shell script

## **_Detailed Installation Processe_**

### Step 1: clone the repo and cd to project root folder

```
git clone https://github.com/Bishwajitkuat/drupal10_mysql_phpmyadmin_template.git
cd drupal10_mysql_phpmyadmin_template
```

### Step 2: if you wish to change container names, mysql db name, user and password, please make that changes in example.env file.

### Step 3: coping .env and .gitignore files

```
mv example.env .env
mv example.gitignore .gitignore
```

### Step 4: if you do not have it please install the followings (only for linux)

```
sudo apt-get install php-xml
sudo apt-get install php-gd
sudo apt-get install php-intl
```

### Step 5: create drupal project with latest drupal

```
composer create-project drupal/recommended-project drupal
```

### Step 6: build the container

```
docker compose up -d
```

- check all the containers are up and running

### Step 7: installing drupal site

- go to: http://localhost:8082/
- go through the installation process

#### Step 7.1: Error: File system: In Verify requirements section (you may encounter)

- Problem: The directory sites/default/files does not exist. An automated attempt to create this directory failed, possibly due to a permissions problem.

- Solution: Reloading the page fixs the problem and create the folder. If it does not fix the problem, please check the permission of the directory

#### Step 7.2: Error: Settings file: In Verify requirements section

- Problem: The Settings file does not exist.

- Solution:

```
cp ./drupal/web/sites/default/default.settings.php ./drupal/web/sites/default/settings.php
```

- When it is get created, reload the page

#### Step 7.3: configur database with the info in .env file

- You may need to click "Advanced options" to see all the fields
- Please replace MYSQL_DATABASE, MYSQL_ROOT_PASSWORD, DB_CONTAINER_NAME with actual values from .env file

```

  database: MYSQL_DATABASE
  username: root
  password: MYSQL_ROOT_PASSWORD
  host: DB_CONTAINER_NAME
  port: 3306

```

Now you would be able to see your new drupal site.

## **_CAUTION:_**

- It will delete any database named "drupalDB" during installation if it's already existed.
- If ports: "3306", "80", "3308", "9082", "8082" are in use by any other services during installation, container related to conflicting port may not install or run.

## quick Installation Processe

some steps in detaile installation procees are combined into a shell file to shorten the installation steps.

### Step 1: clone the repo and cd to project root folder

```
git clone https://github.com/Bishwajitkuat/drupal10_mysql_phpmyadmin_template.git
cd drupal10_mysql_phpmyadmin_template
```

### Step 2: if you wish to change container names, mysql db name, user and password, please make that changes in example.env file.

### Step 4: run the following shell script which perform step 3 to 6

**\*For Linux**

```
./installDrupal_linux.sh
```

**\*For macOS**

```
./installDrupal_macOs.sh
```

### Step 5: follow from step 7 from **_Detailed Installation Processe_**
