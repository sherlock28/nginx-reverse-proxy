FROM node:18-alpine as vue_deps
WORKDIR /app
COPY ./package*.json ./
RUN npm install

FROM vue_deps as vue_src
COPY . .

FROM vue_src as vue_lint
CMD ["npm", "run", "lint"]

FROM vue_src as vue_dev
CMD ["npm", "run", "serve"]

FROM vue_src as vue_build
RUN npm run build

FROM nginx:stable-alpine as final
RUN rm -rf /usr/share/nginx/html/*
COPY --from=vue_build /app/dist /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]
