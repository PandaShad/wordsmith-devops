# ----------------------- BUILD STAGE -----------------------
FROM golang:latest AS build

WORKDIR /src

COPY ./dispatcher.go ./dispatcher.go

RUN go build dispatcher.go

# ----------------------- DEPLOY STAGE -----------------------
FROM ubuntu:latest

WORKDIR /app

COPY ./static ./static
COPY --from=build /src/dispatcher ./dispatcher

EXPOSE 80

CMD [ "/app/dispatcher" ]
