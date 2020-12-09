FROM node:15.3.0-buster-slim

ENV WORKING_DIR=app

WORKDIR /cwd

COPY package*.json /cwd

RUN yarn install

ENTRYPOINT ["yarn", "format"]
