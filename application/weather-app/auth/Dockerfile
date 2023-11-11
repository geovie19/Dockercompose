# builder stage
FROM golang:alpine AS builder
RUN apk add --no-cache git
WORKDIR /go/src/app
RUN git clone https://github.com/abohmeed/weatherapp
WORKDIR /go/src/app/weatherapp/auth/src/main
RUN go build -o /go/bin/app -v ./...

# final stage
FROM alpine:3.14
RUN apk --no-cache add ca-certificates
COPY --from=builder /go/bin/app /app
WORKDIR /app
EXPOSE 8080
CMD ["/app"]
LABEL Name=auth Version=0.0.1

