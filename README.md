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

## Automatic Deploy
### Elastic Beanstalk
1. create application with name `django-circleci` and `DjangoCircleci-env`
1. select `docker` environment and select `64bit amazon linux`
1. set `mysql` database in `Database settings`
1. add `evironment variables` (must be same with `.env.example`)

### Elastic Container Registry
1. create private repo `django`

### CircleCI
1. set up project `django-circleci-aws-eb`
1. select `existed config file`
1. set `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`
1. do code changes, commit and push
1. after, `test-build-deploy` will be `success`

### Check your code change apply or not by accessing `<elastic beanstalk url>/admin/` and `<elastic beanstalk url>/polls/`.