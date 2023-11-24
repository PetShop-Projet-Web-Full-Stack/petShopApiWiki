# Quick Starter Guide

## Introduction

On this page, you will find a quick starter guide
for docker install or Lamps stack.

### Requirement For Lamps Stack

- [PHP 8.2](https://www.php.net/downloads.php)
- [MySQL 8.0](https://dev.mysql.com/downloads/mysql/)
- [Apache 2.4](https://httpd.apache.org/download.cgi)
- [Composer 2.X](https://getcomposer.org/download/)

## Run Api with Docker

### Clone the repository

To clone the repository, you need to run the following command:

```bash
## clone the repository with ssh
git clone git@github.com:PetShop-Projet-Web-Full-Stack/petShopAPI.git

## clone the repository with https
git clone https://github.com/PetShop-Projet-Web-Full-Stack/petShopAPI.git

```

<note>
 You have followed the tutorial to configure Docker on WSL.
    use git clone ssh to clone the repository.
</note>

### Install Docker

First, you need to install docker on your machine.
You can find the installation guide [here, ](https://docs.docker.com/engine/installation/)
Or
You can follow the [tutorial](Tutorial-hot-tow-install-docker-on-WSL.md) to install docker on WSL.

### Install dependencies {id="install-dependencies_1"}

To install the dependencies, you need to run the following command:

```bash
composer install
```

<warning>
    You need to have composer installed on your machine, if you use WSL start linux terminal and run the command.
</warning>

### Create .env file {id="create-env-file_1"}

To create the .env file, you need to run the following command:

```bash
cp .env.example .env
```

> You can change the database name, username and password in the .env file

### Configure your sanctum domain

<warning>
    You need to configure your sanctum domain to use sanctum on your front app.
</warning>

To configure your sanctum domain, you need to go to the .env file and change the following line:

```bash
SANCTUM_STATEFUL_DOMAINS=localhost:3000
```

<warning>
SANCUM_STATEFUL_DOMAINS is the full url of your front app (ex: localhost:3000) 
This will allow you to use sanctum on your front app. if you don't do this, you will send 403 error.
</warning>

### Configure your front url

```bash
FRONT_URL="http://localhost:3000"
```

FRONT_URL is the full url of your front app used for a redirection link in all emails or link sent by the api.

### Configure your mail

To configure your mail, you need to go to the .env file and change the following lines:

```bash
MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=null
MAIL_FROM_NAME="${APP_NAME}"
```

<note>
You can use [mailtrap](https://mailtrap.io/) for development
</note>

### Configure your database

<warning>
    Don't use root for your database username because it will not work.
</warning>
To configure your database you need to go to the .env file and change the following lines:

```bash
DB_CONNECTION=mysql
DB_HOST= [your host]
DB_PORT=3306
DB_DATABASE= [your database name]
DB_USERNAME= [your username]
DB_PASSWORD= [your password]
```

### Generate key {id="generate-key_1"}

To generate the key, you need to run the following command:

```bash
php artisan key:generate
```

### Run docker container with sail

<warning>
    On linux you need to run the command with sudo.
</warning>

To run the api with docker, you need to run the following command:

```bash
./vendor/bin/sail up
```

<note>
  this command will run the api on port 80 and mysql on port 3306.
</note>
### Run migrations {id="run-migrations_1"}

To run the migrations, you need to run the following command:

```bash
./vendor/bin/sail artisan migrate
```

### Run seeders (optional) {id="run-seeders-optional_1"}

This step is optional, it will create fake data in the database.
To run the seeders, you need to run the following command:

```bash
./vendor/bin/sail artisan db:seed
```

### Run tests (optional)

This step is optional, it will run the tests.
To run the tests, you need to run the following command:

```bash
./vendor/bin/sail artisan test
```

### Run api

To run the api, you need to go to the following url:

```bash
http://localhost/
```

**Your Api is now ready to use !**