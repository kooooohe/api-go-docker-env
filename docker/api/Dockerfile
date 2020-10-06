FROM golang:latest as builder
WORKDIR /app
COPY ./api /app
RUN CGO_ENABLED=0 go build -o main main.go
RUN GO111MODULE=off go get github.com/oxequa/realize

FROM alpine:latest as production
RUN apk --no-cache add ca-certificates
WORKDIR /app
COPY --from=builder /app/main /app/main
CMD ["./main"]