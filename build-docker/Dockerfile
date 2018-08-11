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
ENTRYPOINT ["carbon-now-cli"]