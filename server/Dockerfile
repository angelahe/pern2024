FROM node:19-alpine

WORKDIR /home/node/app

COPY . .

RUN chown -R node:node .

USER node

RUN npm install

EXPOSE 9000

CMD [ "node", "index.js" ]