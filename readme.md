# Symfony Development on Docker - Starter Kit

This is a ready-to-use multi comtainer app for symfony app development.

With:

- **PHP (7.2FPM)** - PHP, Composer
- **MySQL** - Database
- **Adminer** - Databse admin UI
- **Nginx** - Web Server
- **MailHog** - email testing

## App Structure

Nginx is set for your Symfony app to be in `app`, with `app/public` being your public facing directory.
You can change this setup in Nginx `default.conf`:
`root /var/www/symfony/app/public`

## Getting started

### Build

Run `docker-compose build` in the `.docker` folder to create the containers.

### Run

Run `docker-compose up` (optionnal flag `-d` for running in the background) to start the app.

### Intalling Symfony template app

In the Php container, in the working directory (`/var/www/symfony`), run :
`> composer create-project symfony/website-skeleton app`
This will set the `app` folder for your Symfony application development, ready for you to code!

## Composer and php bin/console commands

You can run the commands in the php container at `/var/www/symfony/app/`

## More details

### Database URL

In your Symfony `.env` file, set your database url:
`DATABASE_URL="mysql://root:{root password}@{mysql service name}:{mysql docker host port}/{DBNAME}?serverVersion={mysql version}'"`

### Adminer

Accessible under `localhost:1234`
The server name is the Mysql service name from `docker-compose.yml` (_set here to `mysql`_).
Root user password is set to `root` in the `docker-compose.yml`

### MailHog

MailHog is a service to test email sending from your application in dev environment.
You can access the UI at `localhost:8025`.

You'll have to set the `MAILER_DSN` in your `.env` in your Symfony application for the SMTP client to work:
`MAILER_DSN=smtp://mailhog:1025`
More on the [project repo](https://github.com/mailhog/MailHog).
