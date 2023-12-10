FROM ruby:3.2-alpine
# RUN apk update -qq && apk add build-essential libpq-dev mariadb-client


ARG WORKDIR

ARG RUNTIME_PACKAGES="bash icu-data-full icu-libs imagemagick nodejs yarn tzdata mysql-dev mysql-client git"
ARG DEV_PACKAGES="build-base curl-dev"

ENV HOME=/${WORKDIR} \
    TZ=Asia/Tokyo

WORKDIR ${HOME}

COPY Gemfile* ./

RUN apk update && \
    apk upgrade && \
    apk add libpq-dev && \
    apk add --no-cache ${RUNTIME_PACKAGES} && \
    apk add --virtual build-dependencies --no-cache ${DEV_PACKAGES} && \
    bundle install -j4 && \
    apk del build-dependencies

COPY . ./

# 時の運だ。男らしく手動で消せ
# FROM --platform=linux/x86_64 ruby:3.1.2
# COPY entrypoint.sh /usr/bin/
# RUN chmod +x /usr/bin/entrypoint.sh
# ENTRYPOINT ["entrypoint.sh"]

# CMD実行前にentrypoint.shを通す
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

# pumaを起動させる
# CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]
CMD ["rails", "server", "-b", "0.0.0.0"]
