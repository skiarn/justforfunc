#Quick run: docker run --name protoc-cmd --rm -it -u root -v ${PWD}/:/workspace skiarn/protoc sh -c "cd /workspace; sh"
#Takes about 30mins to run build using MacBook Pro Mid 2012 i7.
#docker build -t protoc .
#/workspace/todo # protoc --go_out=. todo.proto
#/workspace/todo # protoc -I . todo.proto --go_out=plugins=grpc:.
#go build -o server ./cmd/server/
#go build -o client ./cmd/todo/
FROM golang:1.9.4-alpine3.7
RUN apk add --update autoconf automake libtool curl make g++ unzip git \ 
    && git clone https://github.com/google/protobuf/ \
    && cd protobuf && ./autogen.sh \
    && ./configure && make && make check && make install \
    && go get -u github.com/golang/protobuf/protoc-gen-go \
    && rm -rf /go/protobuf
