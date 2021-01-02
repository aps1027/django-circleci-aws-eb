# Django CircleCI AWS Elastic Beanstalk

## Prerequisites
1. install `docker`
1. install `docker-compose`

## Local Project Setup
1. start `docker-compose`
    ```
    $ docker-compose up -d
    ```
1. create `.env` file
    ```
    $ cp web/.env.example web/.env
    ```
1. db migrate
    ```
    $ docker-compose exec web python manage.py migrate
    ```
1. collect statci files
    ```
    $ docker-compose exec web python manage.py collectstatic
    ```