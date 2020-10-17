FROM ruby as build

WORKDIR /app
COPY . /app

RUN bundle install
RUN bundle exec jekyll build

FROM nginx:stable-alpine    

COPY --from=build /app/_site /frontend

CMD nginx -g "daemon off;"
COPY nginx.conf /etc/nginx/