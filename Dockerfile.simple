FROM golang:1.21 AS builder
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN go build -o app main.go
FROM debian:bullseye-slim
WORKDIR /root/
COPY --from=builder /app/app .
COPY --from=builder /app/templates ./templates
CMD ["./app"]
