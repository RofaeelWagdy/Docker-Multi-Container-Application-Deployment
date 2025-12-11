# get base image
FROM node:slim

# select working directory
WORKDIR /app

# install dependencies
COPY package.json ./
RUN npm install

# copy source code files
COPY . .

# expose port
EXPOSE 5173

# commands for running
CMD ["npm", "run", "dev", "--", "--host"]