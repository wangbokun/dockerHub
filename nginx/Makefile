DOCKER_NAME=nginx
Hub_Addr=xxxx.com/public

APP_VER=latest
SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}

build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .
run:
	mkdir -p ${SHARE_PATH}/www
	mkdir -p ${SHARE_PATH}/conf
	mkdir -p ${SHARE_PATH}/logs

	docker run  -p 8082:80 --name runoob-nginx-test-web \ 
	-v ${SHARE_PATH}/www:/usr/share/nginx/html \
	-v ${SHARE_PATH}/conf/nginx.conf:/etc/nginx/nginx.conf \ 
	-v ${SHARE_PATH}/logs:/var/log/nginx  -d ${DOCKER_NAME}:${APP_VER} nginx
	


push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 