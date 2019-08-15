DOCKER_NAME=etcd
Hub_Addr=xxxx.com/public

APP_VER=v3.3.13
GITHUB_URL=https://github.com/etcd-io/etcd/releases/download
DOWNLOAD_URL=${GITHUB_URL}
DOWNLOAD_LOCAL_PATH=./files

name=kun
SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}


mkPath:
	mkdir -p ${DOWNLOAD_LOCAL_PATH}	

download: 
	# curl -L ${DOWNLOAD_URL}/${APP_VER}/etcd-${APP_VER}-linux-amd64.tar.gz -o ${DOWNLOAD_LOCAL_PATH}/etcd-${APP_VER}-linux-amd64.tar.gz
	tar xzvf ${DOWNLOAD_LOCAL_PATH}/etcd-${APP_VER}-linux-amd64.tar.gz -C ${DOWNLOAD_LOCAL_PATH} --strip-components=1

build: mkPath	download
	docker build -t ${DOCKER_NAME}:${APP_VER} .
	# rm -rf ${DOWNLOAD_LOCAL_PATH}

run:
	mkdir -p ${SHARE_PATH}/certs
	mkdir -p ${SHARE_PATH}/data
	docker run   -d -v ${SHARE_PATH}/certs:/etc/ssl/certs -v ${SHARE_PATH}/data:/${name}.etcd \
	-p 4001:4001 -p 2380:2380 -p 2379:2379 \
 	--name etcd ${DOCKER_NAME}:${APP_VER}   /usr/local/bin/etcd --name ${name} 	 --listen-client-urls http://0.0.0.0:2379   --advertise-client-urls http://0.0.0.0:2379  --listen-peer-urls http://0.0.0.0:2380  --initial-advertise-peer-urls http://0.0.0.0:2380    --initial-cluster ${name}=http://0.0.0.0:2380
 push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 