FROM node:14.15.4-alpine as builder

# Get the necessary build tools
RUN apk upgrade -U -a \
  && apk add --no-cache \
  autoconf \
  automake \
  build-base \
  libtool \
  nasm \
  pkgconfig \
  && rm -rf /var/cache/* \
  && mkdir /var/cache/apk

# install dependencies
WORKDIR /app
COPY package*.json /app/
RUN npm install

# Get a clean image with cli tools and the pre-built node modules
FROM node:14.15.4-alpine
RUN npm i -g <CLI-TOOL>
COPY --from=builder /app/node_modules /app/node_modules