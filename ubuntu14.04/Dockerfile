FROM ubuntu:14.04

# env vars
ENV HOME /root
ENV GOPATH /go
ENV PATH /go/bin:/usr/local/go/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

# GOPATH
RUN mkdir -p /go

RUN apt-get update
RUN apt-get install -y build-essential mercurial git subversion wget curl

# go 1.3 tarball
RUN wget -qO- http://golang.org/dl/go1.4.2.linux-amd64.tar.gz | tar -C /usr/local -xzf -

RUN go get -u gopkg.in/loom.v1
WORKDIR /go/src/gopkg.in/loom.v1

ENV GOPATH /go/src/gopkg.in/loom.v1/Godeps/_workspace:$GOPATH
RUN go install -v 

ENV LOGXI "*=INF"

ENTRYPOINT ["loom.v1"]
CMD ["-h"]

