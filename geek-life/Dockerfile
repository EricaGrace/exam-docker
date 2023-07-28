
FROM golang:1.20 AS build

WORKDIR /app

COPY ["go.mod", "go.sum", "/app/"]

RUN go mod download

ADD . /app/

RUN go build -o geek-life ./app

#Second stage : run

FROM alpine:latest

WORKDIR /app/

COPY --from=build ./app/geek-life ./geek-life

ENTRYPOINT [ "./geek-life" ]