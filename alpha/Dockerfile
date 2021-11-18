FROM node:lts as alpha
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx as server
EXPOSE 8080
COPY ./nginx/default.conf /etc/nginx/conf.d/defalut.conf
# COPY --from=alpha /app/dist/ /usr/share/nginx/html
COPY --from=alpha /app/dist/ /etc/nginx/html
RUN mkdir /etc/nginx/html/alpha
RUN mv /etc/nginx/html/js /etc/nginx/html/alpha/js
RUN mv /etc/nginx/html/css /etc/nginx/html/alpha/css
RUN mv /etc/nginx/html/img /etc/nginx/html/alpha/img
