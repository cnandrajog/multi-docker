# Specify a base image
FROM node:alpine

# Specify a working directory
WORKDIR '/app'

# Copy package.json from project to docker dir
COPY package.json ./

# Install some dependencies
RUN npm install

# Copy everything else
COPY . .

# start app command using nodemon
CMD ["npm", "run", "start"]