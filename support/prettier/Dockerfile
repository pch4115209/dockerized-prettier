FROM node:15.3.0-buster-slim

COPY package*.json ./

RUN yarn install

WORKDIR app
#
#ENTRYPOINT ["yarn", "check-format"]
