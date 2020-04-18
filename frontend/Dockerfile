FROM node:12.16-alpine

ENV PORT 3000

WORKDIR /application

RUN apk add --no-cache git python && \
    git clone https://github.com/adupays/find-a-pickup-slots.git ./ && \
    npm ci && \
    npm run build

CMD [ "npm", "start" ]

EXPOSE 3000