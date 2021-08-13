# Installation Documentation

Currently, SuperSet is live, at [super-set.ca](https://super-set.ca/). The following instructions can be used to deploy SuperSet onto your local machine or a remote server.

## Installing SuperSet

For **Windows**, install [WAMP](https://www.wampserver.com/en/) (Includes Apache2, MySQL, and PHP)
For **Linux**, install [LAMP](https://bitnami.com/stack/lamp/installer) (Includes Apache2, MySQL, and PHP)

Clone the repository onto your machine: https://github.com/COMP3340-SuperSet/SuperSet.git

### Environment Setup
In the project directory, install:
 - [PHP](https://php.net/) v7.4 or greater
 - [Composer](https://getcomposer.org/) v2.3 or greater
 - [Node](https://nodejs.org/en/) v14 or greater
 - [npm](https://www.npmjs.com/package/npm) v7 or greater

You should verify the version of each before continuing.

Laravel requires an **environment file** to store important application variables. An example is included in the repository, named `.env.example`. 

In the project directory, create a new file, named `.env`. Copy the contents of `.env.example` into `.env`.

### Database Setup
Laravel 8 offers support for the following database systems:
 - MySQL
 - Postgres
 - SQLite
 - SQL Server

You can select any of the above. Our migrations were tested using MySQL, which is packaged with LAMP/WAMP.

Create a database and a schema for superset.
You will need to remember:
 - root user
 - root password
 - schema name

In the `.env` file, you will need to define the following variables to allow Laravel to communicate with your database instance: [Laravel Database Documentation](https://laravel.com/docs/8.x/database)
 - DB_CONNECTION=
 - DB_HOST=
 - DB_PORT=
 - DB_DATABASE=
 - DB_USERNAME=
 - DB_PASSWORD=

### Project Setup

In the project directory, run the following in your terminal:
 - `npm install --save` to install project dependencies
 - `php artisan key:generate` to create an app key for the project
 - `php artisan storage:link` to set up file storage
 - `php artisan migrate` to migrate the superset schema to your database

### Unsplash API Setup (Live Open Data Set)

The live version of [SuperSet](https://super-set.ca/) has Unsplash enabled by default. You can test its functionality here.

To setup Unplash for your local instance of SuperSet, you will need an API key to authorize the application's requests. Apply for one [here](https://unsplash.com/developers).

Place your Unsplash API key in your `.env` file under the variable name `MIX_REACT_APP_UNSPLASH_PUBLIC`.

## Running SuperSet
In the project directory, run the following in your terminal:
 - `npm run dev` to compile the app's JavaScript
 - `php artisan serve` to start the webserver

Running `php artisan serve` will produce a URL in the terminal which points to the app instance.
