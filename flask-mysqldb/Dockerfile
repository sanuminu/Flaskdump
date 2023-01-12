# start by pulling the python image
FROM python:3.7.2-alpine

RUN apk update \
    && apk add --virtual build-deps gcc python3-dev musl-dev \
    && apk add --no-cache mariadb-dev


RUN apk add mysql

# copy the requirements file into the image
COPY ./requirements.txt /app/requirements.txt


# switch working directory
WORKDIR /app

# install the dependencies and packages in the requirements file
RUN pip install -r requirements.txt


# copy every content from the local file to the image

COPY . /app

ENTRYPOINT FLASK_APP=/app/app.py flask run --host=0.0.0.0 --port=5000
