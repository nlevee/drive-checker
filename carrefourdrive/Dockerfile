FROM alpine:3.11 as fetcher

ARG BUILD_VERSION=v0.1.2

RUN apk add --no-cache wget && \
    wget https://github.com/nlevee/go-carrefour-drive-checker/releases/download/${BUILD_VERSION}/go-carrefour-drive-checker_${BUILD_VERSION}_linux_amd64.tar.gz && \
    tar xvzf go-carrefour-drive-checker_${BUILD_VERSION}_linux_amd64.tar.gz

FROM alpine:3.11

WORKDIR /usr/local/bin

RUN apk add --no-cache ca-certificates

COPY --from=fetcher /go-carrefour-drive-checker ./

ENTRYPOINT [ "go-carrefour-drive-checker", "-port", "8080" ]

EXPOSE 8080
