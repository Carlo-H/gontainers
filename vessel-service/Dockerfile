FROM golang:latest as builder

WORKDIR /go/src/github.com/Carlo-H/gontainers/vessel-service

COPY . .

RUN go get -u github.com/golang/dep/cmd/dep
RUN dep init && dep ensure
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo .


FROM debian:latest

RUN mkdir /app
WORKDIR /app
COPY --from=builder /go/src/github.com/Carlo-H/gontainers/vessel-service .

CMD ["./vessel-service"]
