# STEP 1: use golang image to build an executable which will be used in container
FROM golang:alpine AS builder

# Install git since go need git to download packages.
RUN apk update && apk add --no-cache git

# Set current directory in container to copy from host
WORKDIR $GOPATH/src/proxy/

# copy files from given host directory to current folder
COPY src/proxy/ .

# only dowload dependencies of go required for code.
RUN go get -d -v

# build current folder and store executable file.
RUN CGO_ENABLED=0 GOOS=linux go build -o /go/bin/proxy
