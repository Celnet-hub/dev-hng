# syntax=docker/dockerfile:1
# This image is based on the popular Alpine Linux project, available in the alpine official image. Alpine Linux is much smaller than most distribution base images (~5MB), and thus leads to much slimmer images in general.

# this file is a multi-stage build fille


FROM node:19-alpine3.15 as build

LABEL name='Chidubem' email='dubemnwabuisi@gmail.com'

# Create a working directory for Docker to use
WORKDIR /app

# Copy any file dependecies to the image
COPY package*.json ./

# Install app dependencies
RUN yarn install --production
COPY . .
RUN yarn build

# second stage
FROM nginx 
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/build /usr/share/nginx/html