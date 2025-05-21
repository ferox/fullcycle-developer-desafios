FROM golang:1.21-alpine AS builder

RUN apk add --no-cache git

WORKDIR /app

COPY main.go .

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-s -w" -o fullcycle-rocks main.go

FROM scratch

WORKDIR /root/

COPY --from=builder /app/fullcycle-rocks .

CMD ["./fullcycle-rocks"]