DOCKER_NAME=consul
Hub_Addr=xxxx.com/public

APP_VER=1.4.4
SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}

S_IP=10.10.10.1

build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .
run:
	docker run -d -e CONSUL_BIND_INTERFACE='eth0' \ 
	--name=consul_server_2  ${DOCKER_NAME}:${APP_VER}  \
	agent -server -node=2  -join=${S_IP}
	

push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 