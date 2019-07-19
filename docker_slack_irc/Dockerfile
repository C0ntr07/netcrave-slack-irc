FROM node:11.15.0-alpine

COPY docker-entrypoint.sh /usr/local/bin/

RUN mkdir /app && mkdir /config \
    && apk add --no-cache ca-certificates wget tar \
    && wget -O slack-irc.tar.gz https://github.com/ekmartin/slack-irc/archive/master.tar.gz \
    && tar --strip-components=1 -C /app/ -zxf slack-irc.tar.gz \
    && cd /app \
    && npm install && npm run build \
    && rm /slack-irc.tar.gz

ADD docker-entrypoint.sh /app

WORKDIR /app

RUN chmod +x /app/docker-entrypoint.sh

ENTRYPOINT ["/app/docker-entrypoint.sh"]

CMD ["config.json"]

# ENTRYPOINT [ "/bin/sh" ]
