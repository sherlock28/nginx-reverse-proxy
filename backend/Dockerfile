FROM node:18-alpine as deps
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install

FROM deps as final
COPY . .
EXPOSE 3000
CMD ["npm", "start"]