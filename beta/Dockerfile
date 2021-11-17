FROM node:lts as beta
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 8081
COPY ./nginx/default.conf /etc/nginx/conf.d/defalut.conf
COPY --from=beta /app/dist /usr/share/nginx/html