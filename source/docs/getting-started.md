---
title: Getting Started
description: Getting started with DUCS Office Automation
extends: _layouts.documentation
section: content
---

## Getting Started {#getting-started}

This project aims at automating the office work at the Department of Computer Science, University of Delhi (aka DUCS). You can also read the [problem description](../problem-statement/) for more details.

#### **Requirements**

This project is built with Laravel and Alpine.js. The Laravel framework has a few system requirements. All of these requirements are satisfied by the [Laravel Homestead](https://laravel.com/docs/6.x/homestead) virtual machine.

However, if you are not using Homestead, you will need to make sure your local development server meets the following requirements. You can also find these listed in [Laravel Docs](https://laravel.com/docs/6.x#server-requirements).

* PHP >= 7.3.0
* BCMath PHP Extension
* JSON PHP Extension
* Mbstring PHP Extension
* OpenSSL PHP Extension
* PDO PHP Extension
* Tokenizer PHP Extension
* XML PHP Extension

Additionally, you would require to install [Composer](https://getcomposer.org/) and [NPM](https://www.npmjs.com/) to pull in all the project dependencies.

#### **Installation**

###### Using `apt` package manager (Debian/Ubuntu)

Before you begin installing make sure you run `sudo apt update` to get the latest version available.

```bash
# if you do not have MySQL installed on your system
sudo apt install mysql-server

# if you are running Ubuntu 18.04 or older
sudo add-apt-repository ppa:ondrej/php
sudo apt update

# PHP and required extensions
sudo apt install php7.4 php7.4-mysql php7.4-xml php7.4-mbstring php7.4-bcmath php7.4-sqlite php7.4-json

# Composer and NPM
sudo apt install composer npm
```

#### **Quick Start**

* Clone the project using `git`:

```bash
git clone https://github.com/ducs-office/ducs-office-automation.git
```

* Install project dependencies

Go to your project directory and install PHP dependencies using `composer`:

```bash
composer install
```

Use `npm` to install all the required JavaScript dependencies.

```bash
npm install
```

To compile down the front end assets like style sheets (CSS) and JavaScript files, use:

```
npm run dev
```

Or you can also run a watcher to automatically compile the assets, whenever the files are changed.

```
npm run watch
```

* Configure the application

Create a duplicate file of `.env.example` as `.env`.

```bash
cp .env.example .env
```

* Generate an application key using:

```bash
php artisan key:generate
```

> The command will add an application key to your `.env` file.

* Create a new `mysql` user and database

Since the application uses MySQL DBMS, you'd require a database and valid credentials.

```bash
mysql -u root -h localhost -p
```

```bash
mysql> CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
mysql> GRANT ALL PRIVILEGES ON office_automation.* TO 'username'@'localhost' WITH GRANT OPTION;
mysql> ALTER USER 'username'@'localhost' IDENTIFIED WITH mysql_native_password by 'password';
mysql> \q
mysql -u username -h localhost -p
mysql> CREATE DATABASE office_automation;
```

* Setup `Database` connection in `.env` file:

Change the following configuration values:

```bash
...
DB_DATABASE=office_automation
DB_USERNAME=username
DB_PASSWORD=password
...
```

* Add some default data for testing the app

To begin browsing and testing the portal, you'd need the application seeded with some dummy data.

To create all the tables and seed your database with dummy data, run:

```
php artisan migrate --seed
```

* Start Local Development Server

This will serve the project at `localhost:8000`, you can now open this up in your browser using:

```bash
php artisan serve
```

* Default login credentials

Use the following credentials to login as admin

```
Email: admin@cs.du.ac.in
Password: password
```
