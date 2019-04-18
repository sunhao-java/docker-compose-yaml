# Redis
1. copy `./redis` to `${DOCKER_INSTALL}/redis`
        
       cp -r ./ ${DOCKER_INSTALL}/redis
2. modify file `${DOCKER_INSTALL}/redis/docker-compose.yml`

       command: redis-server --appendonly yes --requirepass ${redis_password}
       ports:
         - "${redis_port}:6379"
3. run it

       cd ${DOCKER_INSTALL}/redis
       docker-compose up -d
4. visit redis via `${ip}:${redis_port}` with password `${redis_password}`