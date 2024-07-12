FROM golang:1.20 AS build

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

COPY . .

RUN go build -o /kirito

FROM alpine:latest

RUN apk add --no-cache libc6-compat

COPY --from=build /kirito /kirito

EXPOSE 8080

CMD ["/kirito"]
