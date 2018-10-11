FROM node:8-alpine

WORKDIR /var/www

RUN apk add --no-cache imagemagick
RUN apk add --no-cache curl

COPY package.json yarn.lock ./

RUN apk add --no-cache --virtual .build-deps ca-certificates wget git && \
    yarn install --no-cache && \
    apk del .build-deps

COPY ./ecosystem.json ./
COPY ./config ./config
COPY ./var ./var
COPY ./scripts ./scripts
COPY ./migrations ./migrations
COPY ./src ./src

CMD ["yarn", "start"]
