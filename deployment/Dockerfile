FROM python:3.9-alpine3.15

RUN apk update && apk add --no-cache \ 
gcc git python3-dev libc-dev g++ libffi-dev libxml2 unixodbc-dev  mariadb-dev postgresql-dev

RUN git clone https://github.com/JH7770/pybo.git

COPY .env /pybo/.env

WORKDIR pybo

ENV FLASK_APP="pybo" \
	FLASK_ENV="production" \
	APP_CONFIG_FILE="/pybo/config/production.py"

RUN pip install -r requirements.txt

RUN mkdir logs

ENTRYPOINT ["gunicorn"]
CMD ["--bind", "0:5000", "pybo:create_app()"]
