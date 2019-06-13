FROM node:10-alpine

ARG CACHE_SERVER_VERSION=6.3.0

LABEL org.label-schema.version=${CACHE_SERVER_VERSION}

RUN apk add dumb-init

WORKDIR /srv/unity

ADD https://raw.githubusercontent.com/SpAMCAN/docker-unity-cache-server-ARM/master/6.3.0/entrypoint.sh /srv/unity/
RUN chmod +x /srv/unity/entrypoint.sh

RUN npm i -g unity-cache-server@${CACHE_SERVER_VERSION}

VOLUME [ "/srv/unity/cache" ]
EXPOSE 8126
ENTRYPOINT [ "/srv/unity/entrypoint.sh" ]
CMD [ "unity-cache-server" ]
