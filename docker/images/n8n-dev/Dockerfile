FROM node:16-alpine as builder

USER root

RUN apk --update add --virtual build-dependencies python3 build-base ca-certificates \
  graphicsmagick tzdata git tini su-exec

RUN apk --no-cache add --virtual fonts msttcorefonts-installer fontconfig && \
	update-ms-fonts && \
	fc-cache -f && \
	apk del fonts && \
	find /usr/share/fonts/truetype/msttcorefonts/ -type l -exec unlink {} \;

RUN npm config set python "$(which python3)" && \
	npm config set legacy-peer-deps true && \
	npm install -g lerna full-icu

ENV NODE_ICU_DATA /usr/local/lib/node_modules/full-icu

USER node

ENTRYPOINT ["tini", "--", "/bin/sh"]
