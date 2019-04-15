# Tank
1. copy `./tank` to `${DOCKER_INSTALL}/tank`
        
       cp -r ./ ${DOCKER_INSTALL}/tank
2. modify file `${DOCKER_INSTALL}/tank/docker-compose.yml`

       - "${tank_port}:6010"
3. modify file `${DOCKER_INSTALL}/tank/tank.json`

       {
           "ServerPort": 6010,
           "MatterPath": "",
           "MysqlPort": 3306,
           "MysqlHost": "db",
           "MysqlSchema": "tank",
           "MysqlUsername": "tank",
           "MysqlPassword": "tank123"
       }
3. run it

       cd ${DOCKER_INSTALL}/tank
       docker-compose up -d       
6. visit redis via `http://${ip}:${tank_port}`