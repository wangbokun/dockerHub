DOCKER_TAG=0.0.1
DOCKER_NAME=mysql
Hub_Addr=xxxx.com/public

APP_VER=v3.3.13
GITHUB_URL=https://github.com/etcd-io/etcd/releases/download
DOWNLOAD_URL=${GITHUB_URL}
DOWNLOAD_LOCAL_PATH=./files

SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}


mkPath:
	mkdir -p ${DOWNLOAD_LOCAL_PATH}	

download: 
	curl -L ${DOWNLOAD_URL}/${APP_VER}/etcd-${APP_VER}-linux-amd64.tar.gz -o ${DOWNLOAD_LOCAL_PATH}/etcd-${APP_VER}-linux-amd64.tar.gz
	tar xzvf ${DOWNLOAD_LOCAL_PATH}/etcd-${APP_VER}-linux-amd64.tar.gz -C ${DOWNLOAD_LOCAL_PATH} --strip-components=1

build: mkPath	download
	docker build -t ${DOCKER_NAME}:${DOCKER_TAG} .
	rm -rf ${DOWNLOAD_LOCAL_PATH}

run:
	docker run -d -v ${SHARE_PATH}/:/etc/ssl/certs \
	-p 4001:4001 -p 2380:2380 -p 2379:2379 \
 	--name etcd ${DOCKER_NAME}:${DOCKER_TAG} /usr/local/bin/etcd
push:
	docker tag  ${DOCKER_NAME}:${DOCKER_TAG} ${Hub_Addr}/${DOCKER_NAME}:${DOCKER_TAG}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${DOCKER_TAG}
 