FROM node:14.14.0-alpine as builder
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.15
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html