# MongoDB
1. copy `./mongodb` to `${DOCKER_INSTALL}/mongodb`
        
       cp -r ./ ${DOCKER_INSTALL}/mongodb
2. modify file `${DOCKER_INSTALL}/mongodb/docker-compose.yml`

       mongo:
         environment:
           MONGO_INITDB_ROOT_USERNAME: ${mongo_username}
           MONGO_INITDB_ROOT_PASSWORD: ${mongo_password}
         ports:
           - "${mongo_port}:27017"
       mongo-express:
         ports:
           - ${mongo_express_port}:8081
         environment:
           ME_CONFIG_BASICAUTH_USERNAME: ${mongo_express_username}
           ME_CONFIG_BASICAUTH_PASSWORD: ${mongo_express_password}
           ME_CONFIG_MONGODB_ADMINUSERNAME: ${mongo_username}
           ME_CONFIG_MONGODB_ADMINPASSWORD: ${mongo_password}

3. run it

       cd ${DOCKER_INSTALL}/mongodb
       docker-compose up -d
4. visit mongodb via ` ${mongo_username}:${mongo_password}@${ip}:${mongo_port}`
5. visit mongodb-express via `http://${ip}:${mongo_express_port}`