# LAMP stack built with XDebug built using Docker Compose

This is a basic LAMP stack environment with XDebug built using Docker Compose. It consists following:

* PHP 7.2
* Apache (mod_php)
* MariaDB

## Folder structure

* `bin` - container Dockerfiles
    - `php-apache`
* `config` - container service configurations
    - `apache2` - Apache virtual hosts
    - `php` - PHP config directory
* `logs` - log directory
    - `apache2` - Apache log directory. There can be PHP logs also.
    - `xdebug` - XDebug log directory
    - `mysql` - MySQL log directory
* `www` - project source code

## Installation

1. Make sure you have installed Docker
2. Clone the repository `git clone https://github.com/blry/docker-compose-lamp-xdebug.git`
3. Rename `.env.example` to `.env` and configure
    ##### Must configure
    * `FULL_ROOT_DIR` - full path to the repository. Don't use relative paths and `:` symbol.
        - `/c/Users/alexander.sterpu/Desktop/docker-compose-lamp-xdebug/` (path on Windows)
        - `/repos/docker-compose-lamp-xdebug/` (path on Linux / Mac)
    * `HTTP_PORT` - bind Apache HTTP Server to the port on host machine
    * `MYSQL-*` - MySQL settings
    ##### Optional
    * `APACHE_VHOSTS_DIR` - path to Apache virtual hosts directory
    * `PHP_INI` - path to php.ini file
    * `XDEBUG_REMOTE_PORT` - XDebug remote port. Must not be occupied. 
    * `XDEBUG_IDE_KEY` - XDebug IDE Key option
       - [Configuring XDebug in PhpStorm](https://www.jetbrains.com/help/phpstorm/configuring-xdebug.html#integrationWithProduct)
    * `APACHE_LOG_DIR` - path to the Apache log directory. There can be PHP logs also.
    * `MYSQL_LOG_DIR` - path to the MySQL (MariaDB) log directory
    * `XDEBUG_LOG_DIR` - path to the XDebug log directory
4. If you use Docker for Windows, configure [Docker Shared Drives](https://docs.docker.com/docker-for-windows/#shared-drives) 
5. Run `docker-compose up -d` (`-d` runs container in the background)
6. Done! Now you can access the website via `http://localhost:${HTTP_PORT}`
