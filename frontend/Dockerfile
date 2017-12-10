FROM node:6.11.1-alpine
MAINTAINER David Lemaitre

ENV GULP_VERSION 3.9.1
ENV MODERNIZR_VERSION 3.5.0
ENV BROWSERSYNC_VERSION 2.18.13
ENV YARN_VERSION 1.3.2

ENV NPM_CONFIG_LOGLEVEL warn

# Install requirements
RUN apk add --no-cache \
    git \
    make \
    gcc \
    g++ \
    python \
    automake \
    autoconf \
    nasm \
    zlib-dev

# Install Node packages
RUN npm install -g \
    gulp@"$GULP_VERSION" \
    modernizr@"$MODERNIZR_VERSION" \
    browser-sync@"$BROWSERSYNC_VERSION" \
    yarn@"$YARN_VERSION"

# Expose ports for Browser-Sync
EXPOSE 3000 3001

# Create app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
