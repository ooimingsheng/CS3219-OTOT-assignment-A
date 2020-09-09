FROM node:13.12.0-alpine as build-stage
WORKDIR /app
ENV PATH /app/node_modules/.bin:$PATH
COPY . /app
RUN yarn install
COPY ./ .
RUN yarn build

FROM nginx:1.16.0-alpine
COPY --from=build-stage /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]