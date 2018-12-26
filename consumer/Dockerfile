FROM golang:1.8 as builder

WORKDIR /go/src/app
COPY worker.go .
RUN go get github.com/streadway/amqp && /usr/local/go/bin/go build -o app .

# Application image.
FROM golang:1.8

COPY --from=builder /go/src/app/app /usr/local/bin/app

CMD ["/usr/local/bin/app"]