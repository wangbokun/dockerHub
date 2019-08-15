DOCKER_NAME=mysql
Hub_Addr=xxxx.com/public

APP_VER=5.7
SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}


build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .
run:
	mkdir -p ${SHARE_PATH}
	docker run -p 3306:3306 --name mysql \
	-v ${SHARE_PATH}/conf:/etc/mysql/conf.d \
	-v ${SHARE_PATH}/logs:/logs \
	-v ${SHARE_PATH}/data:/var/lib/mysql \
	-e MYSQL_ROOT_PASSWORD=123456 \
	-d mysql:${APP_VER}

	#mysql -h `hostname`  -P 3306 -u root -p123456

push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 