# Use an official Golang image as the builder stage
FROM golang:1.21-alpine AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy the Go module files first for caching dependencies
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy the rest of the application source code
COPY . .

# Build the Go application
RUN go build -o auth-api .

# Use a minimal base image for production
FROM alpine:latest

# Set the working directory inside the container
WORKDIR /root/

# Copy the compiled binary from the builder stage
COPY --from=builder /app/auth-api .

# Expose the necessary port (change this if your app runs on a different port)
EXPOSE 8081

# Run the application
CMD ["./auth-api"]
