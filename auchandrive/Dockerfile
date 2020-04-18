FROM alpine:3.11 as fetcher

ARG BUILD_VERSION=v0.1.1

RUN apk add --no-cache wget && \
    wget https://github.com/nlevee/go-auchan-drive-checker/releases/download/${BUILD_VERSION}/go-auchan-drive-checker_${BUILD_VERSION}_linux_amd64.tar.gz && \
    tar xvzf go-auchan-drive-checker_${BUILD_VERSION}_linux_amd64.tar.gz

FROM alpine:3.11

WORKDIR /usr/local/bin

RUN apk add --no-cache ca-certificates

COPY --from=fetcher /go-auchan-drive-checker ./

ENTRYPOINT [ "go-auchan-drive-checker", "-port", "8080", "-id" ]

EXPOSE 8080