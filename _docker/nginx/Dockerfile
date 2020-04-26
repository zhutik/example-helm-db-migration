FROM nginx:1.17-alpine

ENV APP_PATH="/example-helm-db-migration"

WORKDIR $APP_PATH

RUN apk add curl

COPY _docker/nginx/_rootfs/ /
COPY . $APP_PATH
