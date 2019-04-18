# Tank
1. copy `./svnadmin` to `${DOCKER_INSTALL}/svnadmin`
        
       cp -r ./ ${DOCKER_INSTALL}/svnadmin
2. modify file `${DOCKER_INSTALL}/svnadmin/docker-compose.yml`

       ports:
         - "${web_port}:8080"
         - "${svn_port}:3690"
       environment:
         SVN_ADMIN_DB: db
         SVN_ADMIN_INSTANCE: svnadmin
         SVN_ADMIN_USERNAME: root
         SVN_ADMIN_PASSWORD: 123456
3. run it

       cd ${DOCKER_INSTALL}/svnadmin
       docker-compose up -d       
4. visit svnadmin via `http://${ip}:${web_port}`
5. visit svn via `svn://${ip}:${svn_port}`