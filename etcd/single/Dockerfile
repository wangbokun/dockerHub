FROM alpine:latest

COPY files/etcd /usr/local/bin/etcd
COPY files/etcdctl /usr/local/bin/etcdctl
RUN mkdir -p /var/etcd/
RUN mkdir -p /var/lib/etcd/

# Alpine Linux doesn't use pam, which means that there is no /etc/nsswitch.conf,
# but Golang relies on /etc/nsswitch.conf to check the order of DNS resolving
# (see https://github.com/golang/go/commit/9dee7771f561cf6aee081c0af6658cc81fac3918)
# To fix this we just create /etc/nsswitch.conf and add the following line:
RUN echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf

EXPOSE 2379 2380

# Define default command.
CMD ["/usr/local/bin/etcd --listen-client-urls http://0.0.0.0:2379 --advertise-client-urls http://0.0.0.0:2379 --listen-peer-urls http://0.0.0.0:2380 --initial-advertise-peer-urls http://0.0.0.0:2380  --initial-cluster my-etcd-1=http://0.0.0.0:2380"]

# ./etcd --name my-etcd-1  --listen-client-urls http://0.0.0.0:2379 --advertise-client-urls http://0.0.0.0:2379 --listen-peer-urls http://0.0.0.0:2380 --initial-advertise-peer-urls http://0.0.0.0:2380  --initial-cluster my-etcd-1=http://0.0.0.0:2380