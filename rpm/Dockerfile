# The "builder" image will build fpm
FROM ruby:2.7.2-alpine AS builder

# fpm's build dependencies
RUN apk update \
  && apk add --update \
  gcc \
  libc-dev \
  libffi-dev \
  make \
  rpm \
  ruby-dev \
  && apk upgrade

RUN echo 'source "https://rubygems.org"; gem "fpm", "~> 1.11.0"' > Gemfile
RUN bundle install

# final image only uses pre-compiled fpm binaries and RPM deps
FROM ruby:2.7.2-alpine

RUN apk update --no-cache \
    && apk upgrade --no-cache \
    && apk add --no-cache rpm

COPY --from=builder /usr/local/bundle/ /usr/local/bundle/

RUN adduser -D fpm-user
USER fpm-user

CMD ["/bin/sh"]
