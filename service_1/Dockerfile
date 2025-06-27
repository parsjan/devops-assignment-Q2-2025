FROM golang:1.24.3-alpine

WORKDIR /app

COPY go.mod .
COPY main.go .

RUN go build -o service_1

EXPOSE 8001
CMD ["./service_1"]
