FROM python:3.9.1-alpine

RUN apk update \
    && apk add --virtual build-deps gcc python3-dev musl-dev \
    && apk add --no-cache mariadb-dev build-base

WORKDIR /work

COPY requirements.txt requirements.txt

RUN python -m pip install -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["gunicorn", "web.wsgi:application", "--bind", "0.0.0.0:8000", "--reload"]