FROM ubuntu as build

ENV TZ=Asia/Shanghai
WORKDIR /app
COPY . /app
RUN apt-get update
RUN apt-get install jekyll bundler -y
RUN bundle install
RUN jekyll build

FROM nginx:stable-alpine    

COPY --from=build /app/site /frontend

CMD nginx -g "daemon off;"
COPY nginx.conf /etc/nginx/