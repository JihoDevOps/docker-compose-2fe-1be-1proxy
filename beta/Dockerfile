FROM node:lts as beta
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx as server
EXPOSE 8081
COPY ./nginx/default.conf /etc/nginx/conf.d/defalut.conf
# COPY --from=beta /app/dist/ /usr/share/nginx/html
# RUN mkdir /usr/share/nginx/html/beta
# RUN mv /usr/share/nginx/html/js/ /usr/share/nginx/html/beta/js/
# RUN mv /usr/share/nginx/html/css/ /usr/share/nginx/html/beta/css/
# RUN mv /usr/share/nginx/html/img/ /usr/share/nginx/html/beta/img/
# COPY --from=alpha /app/dist/ /usr/share/nginx/html
COPY --from=beta /app/dist/ /etc/nginx/html
RUN mkdir /etc/nginx/html/beta
RUN mv /etc/nginx/html/js /etc/nginx/html/beta/js
RUN mv /etc/nginx/html/css /etc/nginx/html/beta/css
RUN mv /etc/nginx/html/img /etc/nginx/html/beta/img