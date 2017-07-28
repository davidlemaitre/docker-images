FROM node:6.11.1-alpine
MAINTAINER David Lemaitre

ENV GULP_VERSION 3.9.1
ENV BOWER_VERSION 1.8.0
ENV MODERNIZR_VERSION 3.5.0
ENV BROWSERSYNC_VERSION 2.18.13

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
  bower@"$BOWER_VERSION" \
  modernizr@"$MODERNIZR_VERSION" \
  browser-sync@"$BROWSERSYNC_VERSION"

# Allow running bower as root
RUN echo '{ "allow_root": true }' > /root/.bowerrc

# Expose Browser-Sync ports
EXPOSE 3000 3001

# Create app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
