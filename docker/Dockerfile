# There's an image at joevandyk/que-web.
# Run like:
# docker run -e DATABASE_URL=postgres://username:password@hostname/db_name -p 3002:8080 joevandyk/que-web

FROM ruby:2.6

WORKDIR /app
ADD . /app

COPY . /app

# Define working directory.
RUN apt-get update && \
    apt-get install libpq-dev -y && \
    rm -rf /var/cache/apt/* /var/lib/apt/lists/* \
    gem install bundler

RUN bundle install

RUN gem install puma

EXPOSE 8080

CMD bundle exec puma -e production -p 8080 /app/config.ru
