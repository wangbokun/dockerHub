DOCKER_NAME=consul
Hub_Addr=xxxx.com/public

APP_VER=1.4.4
SHARE_PATH=/data/share/docker/consul/1.4.4

build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .
run:
	mkdir -p ${SHARE_PATH}
	docker run -d -p 8500:8500  -v ${SHARE_PATH}:/consul/data \
	-e CONSUL_BIND_INTERFACE='eth0' \
	--name=consul_server_1 ${DOCKER_NAME}:${APP_VER} \
	agent -server -bootstrap -ui -node=1 -client='0.0.0.0'
	

push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 