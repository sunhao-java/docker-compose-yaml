# MySQL
1. copy `./mysql` to `${DOCKER_INSTALL}/mysql`
        
       cp -r ./ ${DOCKER_INSTALL}/mysql
2. modify file `${DOCKER_INSTALL}/mysql/docker-compose.yml`

       - "${MYSQL_PORT}:3306"
       - "${MYSQL_ADMIN_PORT}:8080"
3. run it

       cd ${DOCKER_INSTALL}/mysql
       docker-compose up -d
4. visit mysql via `root:123456@${HOSTNAME}:${MYSQL_PORT}`
5. visit mysql-admin via `http://${HOSTNAME}:${MYSQL_ADMIN_PORT}`