FROM node:8.11.3-alpine
RUN apk update && \
    apk upgrade && \
    apk add git
ADD rootfs /rootfs
WORKDIR /rootfs
RUN npm i -g
ENTRYPOINT ["carbon-now-cli"]