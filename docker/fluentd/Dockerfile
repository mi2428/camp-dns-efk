FROM fluent/fluentd:v1.7-1
LABEL maintainer "mi2428 <tmiya@protonmail.ch>"

ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

USER root

RUN apk add --no-cache --update --virtual .build-deps \
      build-base ruby-dev \
 && apk add --no-cache --update \
      geoip geoip-dev automake autoconf libtool \
      python3 \
 && pip3 install geoip2 dnspython \
 && gem install fluent-plugin-http-heartbeat \
 && gem install fluent-plugin-elasticsearch \
 && gem install fluent-plugin-geoip \
 && gem sources --clear-all \
 && apk del .build-deps \
 && rm -rf \
      /tmp/* \
      /var/tmp/* \
      /var/cache/apk/* \
      /usr/lib/ruby/gems/*/cache/*.gem

USER fluent
