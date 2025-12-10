# select base image
FROM mysql:8.0.44-debian

# select workdir
WORKDIR /docker-entrypoint-initdb.d

# copy code files
COPY init.sql /docker-entrypoint-initdb.d/

# set environment variables
ENV MYSQL_ROOT_PASSWORD=1234