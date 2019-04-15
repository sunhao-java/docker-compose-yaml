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