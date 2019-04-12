> example env:

	# docker
	export DOCKER_INSTALL=/home/docker/docker-install
	export DOCKER_VOLUME=/home/docker/docker-volume

# Harbor
1. copy `./harbor` to `${DOCKER_INSTALL}/harbor`

       cp -r ./harbor/ ${DOCKER_INSTALL}/
2. modify file `${DOCKER_INSTALL}/harbor/docker-compose.yml`

       - ${PORT}:80
       - 443:443
       - 4443:4443
3. modify file `${DOCKER_INSTALL}/harbor/config/adminserver/env`

       EXT_ENDPOINT=http://${HOSTNAME}:${PORT}
       ...
       EMAIL_HOST=${EMAIL_HOST}
       EMAIL_PORT=${EMAIL_PORT}
       EMAIL_USR=${EMAIL_USR}
       EMAIL_PWD=${EMAIL_PWD}
	   EMAIL_SSL=false
       EMAIL_FROM=Harbor <${EMAIL_USR}>
       EMAIL_IDENTITY=
       EMAIL_INSECURE=false
4. modify file `${DOCKER_INSTALL}/harbor/config/registry/config.yml`

       auth:
         token:
           issuer: harbor-token-issuer
           realm: http://${HOSTNAME}:${PORT}/service/token
           rootcertbundle: /etc/registry/root.crt
           service: harbor-registry
5. run it

       cd ${DOCKER_INSTALL}/harbor
       docker-compose up -d
6. data in `${DOCKER_VOLUME}/harbor`
7. visit via `http://${HOSTNAME}:${PORT}`

# MySQL
1. copy `./mysql` to `${DOCKER_INSTALL}/mysql`
        
       cp -r ./mysql/ ${DOCKER_INSTALL}/
2. modify file `${DOCKER_INSTALL}/mysql/docker-compose.yml`

       - "${MYSQL_PORT}:3306"
       - "${MYSQL_ADMIN_PORT}:8080"
3. run it

       cd ${DOCKER_INSTALL}/mysql
       docker-compose up -d
4. visit mysql via `root:123456@${HOSTNAME}:${MYSQL_PORT}`
5. visit mysql-admin via `http://${HOSTNAME}:${MYSQL_ADMIN_PORT}`

# ELK(`E`lasticsearch + `L`ogstash + `K`ibana)
1. copy `./elk` to `${DOCKER_INSTALL}/elk`
        
       cp -r ./elk/ ${DOCKER_INSTALL}/
2. modify file `${DOCKER_INSTALL}/elk/docker-compose.yml`

       - "${ES_PORT}:9200"
       - "${LOGSTASH_PORT}:9250"
       - "${KIBANA_PORT}:5601"
3. run it

       cd ${DOCKER_INSTALL}/elk
       docker-compose up -d
4. visit kibana via `http://ip:${KIBANA_PORT}`
5. push log to logstash via `ip:${LOGSTASH_PORT}`
6. visit elasticsearch via `ip:${ES_PORT}` with no password!