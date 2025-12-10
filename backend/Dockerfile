# get base image
FROM node:slim

# select working directory
WORKDIR /app

# copy code files
COPY server.js .

# install dependencies
RUN npm install express mysql2 cors body-parser csv-writer

# expose ports
EXPOSE 3000

# commands for running
CMD [ "node", "server.js" ]