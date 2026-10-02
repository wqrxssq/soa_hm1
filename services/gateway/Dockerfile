FROM golang:1.27-alpine AS build

WORKDIR /src
COPY go.mod ./
COPY *.go ./
RUN CGO_ENABLED=0 go build -o /out/gateway .

FROM alpine:3.22
COPY --from=build /out/gateway /gateway
EXPOSE 8080
USER nobody
ENTRYPOINT ["/gateway"]
