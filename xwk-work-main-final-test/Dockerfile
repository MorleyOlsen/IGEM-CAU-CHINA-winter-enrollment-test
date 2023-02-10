FROM node:16-alpine  as build-stage
WORKDIR /code
ADD package.json /code/
RUN npm install --registry=https://registry.npm.taobao.org

ADD . /code
RUN npm run build


FROM nginx:stable-alpine as production-stage

COPY --from=build-stage /code/dist /usr/share/nginx/html
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]