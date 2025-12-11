# get base image
FROM node:slim

# select working directory
WORKDIR /app

# install dependencies
RUN npm install express mysql2 cors body-parser csv-writer

# copy code files
COPY server.js .
RUN mkdir data

# expose ports
EXPOSE 3000

# commands for running
CMD [ "node", "server.js" ]