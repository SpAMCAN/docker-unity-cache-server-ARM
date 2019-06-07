FROM node:10-alpine

ARG CACHE_SERVER_VERSION=6.3.0

LABEL org.label-schema.version=${CACHE_SERVER_VERSION}

# Update packages and install software
RUN apt-get update \
    && curl -sLO https://archive.raspbian.org/raspbian/pool/main/d/dumb-init/dumb-init_1.0.3-1_armhf.deb \
    && dpkg -i dumb-init_*.deb \
    && rm -rf dumb-init_*.deb \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /srv/unity

COPY entrypoint.sh entrypoint.sh

RUN npm i -g unity-cache-server@${CACHE_SERVER_VERSION}

VOLUME [ "/srv/unity/cache" ]
EXPOSE 8126
ENTRYPOINT [ "/srv/unity/entrypoint.sh" ]
CMD [ "unity-cache-server" ]
