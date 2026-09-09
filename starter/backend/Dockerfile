FROM python:3.10-alpine

ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /app

RUN apk add --no-cache \
    build-base \
    gcc \
    linux-headers \
    openssl \
    libffi-dev \
    pcre \
    pcre-dev

RUN pip install --no-cache-dir pipenv

COPY Pipfile Pipfile.lock /app/

RUN pipenv install --system --deploy

COPY . /app

EXPOSE 5000

CMD ["flask", "--app", ".", "run", "--host=0.0.0.0", "--port=5000"]