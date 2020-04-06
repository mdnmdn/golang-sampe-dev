FROM golang:1.13-alpine as build

RUN apk --update add git && \
    rm -rf /var/lib/apt/lists/* && \
    rm /var/cache/apk/* && \
    go get github.com/githubnemo/CompileDaemon github.com/go-delve/delve/cmd/dlv



#/go/bin/CompileDaemon

FROM golang:1.13-alpine as app

COPY --from=build /go/bin/CompileDaemon /go/bin/dlv /go/bin/
# COPY --from=build /go/bin/dlv /go/bin/
RUN apk add --no-cache libc6-compat && \
    rm -rf /var/lib/apt/lists/* && \    
    mkdir /app

# ENV HOME /app
ENV CGO_ENABLED 0

WORKDIR /app

#CMD ["sh"]

# docker build  -t mdnmdn/golang-compile-daemon:1.13-alpine .
# docker push mdnmdn/golang-compile-daemon:1.13-alpine