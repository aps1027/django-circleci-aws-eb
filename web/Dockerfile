FROM python:3.9.1-alpine

RUN apk update \
    && apk add --virtual build-deps gcc python3-dev musl-dev \
    && apk add --no-cache mariadb-dev build-base

COPY requirements.txt requirements.txt

RUN python -m pip install -r requirements.txt

COPY . .