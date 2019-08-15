DOCKER_NAME=grafana
Hub_Addr=xxxx.com/public

APP_VER=6.2.5
SHARE_PATH=/data/share/docker/grafana/5.6

build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .
run:
	docker run  \
	 -d --name=grafana -p 3000:3000  \
	  ${DOCKER_NAME}:${APP_VER}


push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 