FROM node:alpine
WORKDIR '/app'
COPY ./package*.json ./
RUN npm install -s --prefer-offline --no-audit
COPY ./ ./

RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html