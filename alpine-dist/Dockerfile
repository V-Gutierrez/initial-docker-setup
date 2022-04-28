# build phase

FROM node:12-stretch AS aliasedbuild

WORKDIR /build

COPY package.json package-lock.json ./

RUN npm ci

COPY . .

# runtime phase (without package bundler npm e.g.)

FROM alpine:3.10

RUN apk add --update nodejs

RUN addgroup -S node && adduser -S node -G node

USER node

RUN mkdir /home/node/code

WORKDIR /home/node/code

COPY --from=aliasedbuild --chown=node:node /build .

CMD ["node", "index.js"]