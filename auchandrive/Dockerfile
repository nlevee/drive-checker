FROM alpine as fetcher

RUN apk add --no-cache wget && \
    wget https://github.com/nlevee/go-auchan-drive-checker/releases/download/v0.1.1/go-auchan-drive-checker_v0.1.1_linux_amd64.tar.gz && \
    tar xvzf go-auchan-drive-checker_v0.1.1_linux_amd64.tar.gz

FROM alpine 

WORKDIR /usr/local/bin

RUN apk add --no-cache ca-certificates

COPY --from=fetcher /go-auchan-drive-checker ./

ENTRYPOINT [ "go-auchan-drive-checker", "-port", "8080", "-id" ]

EXPOSE 8080