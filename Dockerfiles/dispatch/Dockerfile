# Stage 1 - BUILD
FROM golang:1.23 AS build

WORKDIR /app

# Copy source code
COPY *.go .

# Initialize module and download dependencies
RUN go mod init dispatch && go mod tidy

# Build binary
RUN go build -o main .

# Stage 2 - RUN
FROM alpine:latest

WORKDIR /app

EXPOSE 8080

# Copy binary from build stage
COPY --from=build /app/main .

CMD ["./main"]




