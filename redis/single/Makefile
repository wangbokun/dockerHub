DOCKER_NAME=redis
Hub_Addr=xxxx.com/public

APP_VER=3.2
SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}

build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .
run:
	mkdir -p ${SHARE_PATH}/data

	docker run -p 6379:6379 -v ${SHARE_PATH}/data:/data  \
	-d ${DOCKER_NAME}:${APP_VER} redis-server --appendonly yes	
	# 需要密码的话，打开这一行，上一行记得加上 '\'
	# --requirepass "123456" 

push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 