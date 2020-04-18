FROM node:12.16-alpine

ENV PORT 3000

WORKDIR /application

RUN apk --no-cache --virtual build-dependencies add \
    git \
    python \
    make \
    g++ && \
    git clone https://github.com/adupays/find-a-pickup-slots.git ./ && \
    npm ci && \
    npm run build && \
    apk del build-dependencies

CMD [ "npm", "start" ]

EXPOSE 3000