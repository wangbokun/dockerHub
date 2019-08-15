DOCKER_NAME=mongo
Hub_Addr=xxxx.com/public

APP_VER=3.2
SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}


build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .
run:
	mkdir -p ${SHARE_PATH}/db
	docker run -p 27017:27017 -v ${SHARE_PATH}/db:/data/db \
	-d ${DOCKER_NAME}:${APP_VER}

push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 