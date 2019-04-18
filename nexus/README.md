# Nexus
1. copy `./nexus` to `${DOCKER_INSTALL}/nexus`
        
       cp -r ./ ${DOCKER_INSTALL}/nexus
2. modify file `${DOCKER_INSTALL}/nexus/docker-compose.yml`

       - "${nexus_port}:8081"
3. run it

       cd ${DOCKER_INSTALL}/nexus
       docker-compose up -d
4. visit nexus via `http://${ip}:${nexus_port}`