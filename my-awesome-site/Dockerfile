FROM ruby as build

# ENV DEBIAN_FRONTEND=noninteractive
# ENV TZ=Asia/Shanghai

WORKDIR /app
COPY . /app
RUN ln -fs /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata
RUN bundle install
RUN bundle exec jekyll build

FROM nginx:stable-alpine    

COPY --from=build /app/_site /frontend

CMD nginx -g "daemon off;"
COPY nginx.conf /etc/nginx/