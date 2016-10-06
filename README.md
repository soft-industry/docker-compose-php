# docker-compose-php

Docker Compose setup to run php5.3, php5.6 or php7 with php-fpm via nginx and mysql.

# Purpose

Create the ultimate development environment.

# Install

Install Docker and [docker-compose](https://docs.docker.com/compose/install/).
On Windows 10 install Docker Toolbox and [disable Hyper-V](http://www.poweronplatforms.com/enable-disable-hyper-v-windows-10-8/).

# Project setup

* The webroot is at ./app/web
* You can put initial MySQL dump to the ./mysql/dump directory, it will be applied at the db container build. Format `*.sql` or `*.sql.gz`. Use `dump.sql.example` as an example.
* The MySQL data will be stored at the ./mysql/databases directory. So data will be persistent between docker-compose runs.
* The MySQL root password is at docker-compose.yml
* Database access is
  host: db
  user: root
  password: (password from docker-compose.yml)
  database name: (name from dump in ./mysql/dump)

# Run

* On Linux.
	- `git clone https://github.com/soft-industry/docker-compose-php.git`
	- `cd docker-compose-php`
	- `docker-compose build`
	- `docker-compose up -d`
* On Windows 10.
	- Place the project within the Users directory
	- Open Docker quickstart terminal
	- Using command prompt navigate to the project directory
	- Run `docker-compose build` and `docker-compose up -d` as usual

# PHP

By default the setup creates a php5.6 environment, see docker-compose-php-7.yml how to use php7.

# Test

* On Linux.
	- Open url http://localhost:8000
* On Windows 10.
	- In the Docker quickstart terminal run `docker-machine ls`
	- Open the ip of your docker machine with port 8000.

# Command reference

* `docker-compose exec db bash` will open shell on the running db container.
* `docker-compose stop` will stop running containers.
* `docker-compose rm db` will erase built db container. So when you run `docker-compose up` it will be built again, and the initial dump will apply.
* `$ docker exec some-mysql-contaner sh -c 'exec mysqldump -uroot -p"$MYSQL_ROOT_PASSWORD" db_name' > /some/path/on/your/host/db_name.sql` will make dump from `some-mysql-contaner` and database `db_name` into local file.
