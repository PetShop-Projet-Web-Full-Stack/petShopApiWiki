# Quick Starter Guide

## Introduction

On this page you will find a quick starter guide
for docker install or Lamps stack.

### Requirement For Lamps Stack

- [PHP 8.2](https://www.php.net/downloads.php)
- [MySQL 8.0](https://dev.mysql.com/downloads/mysql/)
- [Apache 2.4](https://httpd.apache.org/download.cgi)
- [Composer 2.X](https://getcomposer.org/download/)

## Run Api with Lamps Stack

### Install lamp stack

First you need to install lamp stack on your machine.
You can find the installation
guide [here](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04).

> You can also use [Xampp](https://www.apachefriends.org/fr/index.html) or [Wamp](https://www.wampserver.com/en/)

### Install dependencies

To install the dependencies you need to run the following command:

```bash
composer install
```

### Create .env file

To create the .env file you need to run the following command:

```bash
cp .env.example .env
```
<note>
 You can change the database name, username and password in the .env file
</note>

### Generate key

To generate the key you need to run the following command:

```bash
php artisan key:generate
```

### Run migrations

To run the migrations you need to run the following command:

```bash
php artisan migrate
```

### Run seeders (optional)

this step is optional, it will create fake data in the database.
To run the seeders you need to run the following command:

```bash
php artisan db:seed
```

## Run Api with Docker (Recommended for development)

### Install Docker

First you need to install docker on your machine.
You can find the installation guide [here](https://docs.docker.com/engine/installation/).

### Install dependencies {id="install-dependencies_1"}

To install the dependencies you need to run the following command:

```bash
composer install
```

### Create .env file {id="create-env-file_1"}

To create the .env file you need to run the following command:

```bash
cp .env.example .env
```

> You can change the database name, username and password in the .env file

### Generate key {id="generate-key_1"}

To generate the key you need to run the following command:

```bash
php artisan key:generate
```

### Run docker container with sail

To run the api with docker you need to run the following command:

```bash
./vendor/bin/sail up
```

### Run migrations {id="run-migrations_1"}

To run the migrations you need to run the following command:

```bash
./vendor/bin/sail artisan migrate
```

### Run seeders (optional) {id="run-seeders-optional_1"}

this step is optional, it will create fake data in the database.
To run the seeders you need to run the following command:

```bash
./vendor/bin/sail artisan db:seed
```

### Run tests (optional)

this step is optional, it will run the tests.
To run the tests you need to run the following command:

```bash
./vendor/bin/sail artisan test
```

### Run api

To run the api you need to go to the following url:

```bash
http://localhost/
```

## Configure your sanctum domain

To configure your sanctum domain you need to go to the .env file and change the following line:

```bash
SANCTUM_STATEFUL_DOMAINS=localhost:3000
```

<warning>
SANCUM_STATEFUL_DOMAINS is the full url of your front app (ex: localhost:3000) 
This will allow you to use sanctum on your front app. if you don't do this you will send 403 error.
</warning>

## Configure your front url

```bash
FRONT_URL="http://localhost:3000"
```

FRONT_URL is the full url of your front app used for redirection link in all email or link sent by the api.

## Configure your mail

To configure your mail you need to go to the .env file and change the following lines:

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

## Configure your database

To configure your database you need to go to the .env file and change the following lines:

```bash
DB_CONNECTION=mysql
DB_HOST= [your host]
DB_PORT=3306
DB_DATABASE= [your database name]
DB_USERNAME= [your username]
DB_PASSWORD= [your password]
```

**Your Api is now ready to use !**