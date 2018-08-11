FROM node:8.11.3-alpine
RUN apk update && \
    apk upgrade && \
    apk add git openssh
RUN npm install -g npm@latest
ADD rootfs /rootfs
WORKDIR /rootfs
RUN rm .git
RUN git init
RUN npm install -g
RUN \
  echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories \
  && echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories \
  && echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
  && apk --no-cache  update \
  && apk --no-cache  upgrade \
  && apk add --no-cache --virtual .build-deps \
    gifsicle pngquant optipng libjpeg-turbo-utils \
    udev ttf-opensans chromium \
  && rm -rf /var/cache/apk/* /tmp/*
WORKDIR /tmp
ENTRYPOINT ["carbon-now"]