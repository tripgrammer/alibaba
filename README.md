# Internet Engineering Project

Alibaba is a simple application written by Python3 & Django2.2. This project is for Internet Engineering Course.

##  Demo
[Final project preview.](https://i.imgur.com/KJ66n8T.jpg)

## Technologies used in this course

This project and video series are best practices for Backend Engineering with Python and Django and the most common technologies every backend engineer should know. Technologies used in this course are listed below.
-   [Python 3.x](https://www.python.org/) - Programming Language
-   [Django 2.2.x](https://www.djangoproject.com/) - Powerful Web Framework
-   [Gunicorn](https://gunicorn.org/) - WSGI HTTP Server
-   [PostgreSQL](https://www.postgresql.org/) - PostgreSQL Database
-   [NginX](https://www.nginx.com/) - High performance web server
-   [Docker](https://www.docker.com/) - Container Platform
-   [ArvanCloud](https://www.arvancloud.com/) - Integrated Cloud Infrastructure
-   [GitHub](https://github.com/) - Version Control

##  Installation
First **clone** or **download** this project.
```sh
$ https://github.com/tripgrammer/alibaba.git
```
Then create **docker network** and **volumes** as below.

```sh
$ docker volume create blogpy_postgresql
$ docker volume create blogpy_static_volume
$ docker volume create blogpy_files_volume
```
```sh
$ docker network create nginx_network
$ docker network create blogpy_network
```
You need to create .env file in the project root file with default values.
```sh
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=postgres
```
Now run django and postgresql with **docker-compose**.
```sh
$ docker-compose up -d
```
Then run nginx container with **docker-compose**.
```sh
$ cd config/nginx/
$ docker-compose up -d
```
You can see blogpy web page on http://localhost, Template and API's are accessable by  docker containers which you can see with below command.
```sh
$ docker ps -a
```
**Output** should be like this.
```sh
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
fc6cc9d6d3d7        nginx_nginx         "nginx -g 'daemon of…"   2 hours ago         Up 2 hours          0.0.0.0:80->80/tcp       nginx
05103904dcb8        ae80efb17475        "gunicorn --chdir bl…"   2 hours ago         Up 2 hours          0.0.0.0:8000->8000/tcp   blogpy
4a183e90a9eb        postgres:10         "docker-entrypoint.s…"   2 hours ago         Up 2 hours          0.0.0.0:5432->5432/tcp   blogpy_postgresql
```
**nginx** container as common web server, **blogpy** container as django application and **blogpy_postgresql** as postgreSQL database container.

## Contributing
Contributions are  **welcome**  and will be fully  **credited**. I'd be happy to accept PRs for template extending.
