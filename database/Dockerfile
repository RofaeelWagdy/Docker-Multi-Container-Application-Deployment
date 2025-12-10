FROM mysql:8.0.44-debian

WORKDIR /docker-entrypoint-initdb.d

COPY init.sql /docker-entrypoint-initdb.d/

ENV MYSQL_ROOT_PASSWORD=1234