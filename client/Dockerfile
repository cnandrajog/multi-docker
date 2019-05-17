# This is a multi-step build docker file for production
# Specify a base image for builder phase
FROM node:alpine as builder

# Specify a working directory
WORKDIR '/app'

# Copy packageTest.json from project to docker dir
COPY ./client/package.json ./

# Install  dependencies
RUN npm install

# Copy everything else
COPY . .

# build the code for production env
RUN npm run build

#Phase 2
# Specify a base image where production app will run
FROM nginx

#Exposing port
EXPOSE 3000


# Copying nginx file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# Copying the build output from the builder plase to nginx folder
COPY --from=builder /app/build /usr/share/nginx/html