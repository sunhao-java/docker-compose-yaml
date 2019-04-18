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
4. run it

       cd ${DOCKER_INSTALL}/tank
       docker-compose up -d       
5. visit tank via `http://${ip}:${tank_port}`