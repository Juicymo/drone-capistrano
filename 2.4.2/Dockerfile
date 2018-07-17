# Docker image for the Drone Capistrano plugin
#
#     cd $GOPATH/src/github.com/drone-plugins/drone-capistrano
#     make deps build docker

FROM juicymo/drone-ruby:2.4.2
MAINTAINER Tomas Jukin <tomas.jukin@juicymo.cz>

ENV BUILD_PACKAGES="ca-certificates git openssh" \
    DEV_PACKAGES="zlib-dev libxml2-dev libxslt-dev tzdata yaml-dev sqlite-dev postgresql-dev"

RUN \
  apk add --update --upgrade $BUILD_PACKAGES $DEV_PACKAGES && \
  find / -type f -iname \*.apk-new -delete && \
  rm -rf /var/cache/apk/* && \
  rm -rf /usr/lib/ruby/gems/*/cache/* && \
  rm -rf /usr/local/bundle/cache/* && \
  rm -rf ~/.gem

ADD bundle.sh /
ADD drone-capistrano /bin/
ENTRYPOINT ["/bin/drone-capistrano"]
