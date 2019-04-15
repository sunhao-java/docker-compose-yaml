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