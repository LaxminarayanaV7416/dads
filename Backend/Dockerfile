FROM python:3.10-alpine

WORKDIR /code
COPY requirements.txt /code
RUN --mount=type=cache,target=/root/.cache/pip \
    pip3 install -r requirements.txt

COPY . .

ENV POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
ENV POSTGRES_DB=${POSTGRES_DB}
ENV POSTGRES_USER=${POSTGRES_USER}
ENV DB_HOST_FOR_BACKEND=${DB_HOST_FOR_BACKEND}
ENV DB_PORT_FOR_BACKEND=${DB_PORT_FOR_BACKEND}

ENV FLASK_APP server.py
ENV FLASK_ENV development
ENV FLASK_RUN_PORT=${BACKEND_PORT}
ENV FLASK_RUN_HOST 0.0.0.0

EXPOSE ${BACKEND_URL}

CMD ["flask", "run"]