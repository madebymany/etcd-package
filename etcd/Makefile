GIT_URL:=https://github.com/coreos/etcd.git
ETCD_SOURCE:=etcd
GO_PATH:=/usr/local/go

all: $(GO_PATH) $(ETCD_SOURCE) build

$(GO_PATH):
	curl -LSOs http://golang.org/dl/go1.2.2.linux-amd64.tar.gz
	tar -C /usr/local -xf go1.2.2.linux-amd64.tar.gz

$(ETCD_SOURCE):
	git clone $(GIT_URL)

build:
	export PATH=$$PATH:/usr/local/go/bin && echo $$PATH && cd etcd && echo $$(pwd) && /bin/bash < build

install:
	install -o root -g root $(ETCD_SOURCE)/bin/etcd /usr/local/bin
	install -D -o root -g root etc/sv/etcd/run /etc/sv/etcd/run
	install -o root -g root etc/default/etcd /etc/default

.PHONY: build
