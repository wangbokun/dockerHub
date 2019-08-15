APP_VER=latest
DOCKER_NAME=etcdkeeper
Hub_Addr=xxxx.com/public

# S_IP=127.0.0.1
# S_PORT=2379


SHARE_PATH=/data/share/docker/${DOCKER_NAME}/${APP_VER}


build:
	docker build -t ${DOCKER_NAME}:${APP_VER} .

run:
	docker run --rm -it -d --name etcdkeeper \
	-p 0.0.0.0:9000:8080 \
	-t -i ${DOCKER_NAME}:${APP_VER}

	# docker run --rm --name etcd-browser -p 0.0.0.0:8000:8000  --env ETCD_HOST=${S_IP} --env AUTH_PASS=doe -t -i ${DOCKER_NAME}:${APP_VER}

push:
	docker tag  ${DOCKER_NAME}:${APP_VER} ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}

	docker push ${Hub_Addr}/${DOCKER_NAME}:${APP_VER}
 