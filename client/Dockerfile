FROM node:19-alpine

WORKDIR /home/node/app

COPY . .

RUN chown -R node:node .

USER node

RUN npm install

EXPOSE 3000

CMD [ "npm", "start" ]