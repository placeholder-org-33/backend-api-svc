FROM golang:1.23-alpine AS builder

WORKDIR /app

COPY go.mod ./
COPY go.sum ./
RUN go mod download

COPY *.go ./

RUN go build -o /user-api

FROM alpine:latest

WORKDIR /root/

COPY --from=builder /user-api ./

EXPOSE 3000

CMD ["./user-api"]
