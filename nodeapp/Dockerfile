FROM node:12-stretch

USER node

RUN mkdir /home/node/code

WORKDIR /home/node/code

RUN npm ci

COPY --chown=node:node . .

CMD ["node", "index.js"]

EXPOSE 3000