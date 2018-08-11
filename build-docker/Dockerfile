FROM node:8.11.3-alpine
ADD rootfs /rootfs
WORKDIR /rootfs
RUN npm i -g
ENTRYPOINT ["carbon-now-cli"]