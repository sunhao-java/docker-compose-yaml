# gitlab
1. copy `./` to `${DOCKER_INSTALL}/gitlab`
        
       cp -r ./ ${DOCKER_INSTALL}/gitlab
2. modify file `${DOCKER_INSTALL}/gitlab/docker-compose.yml`

       - "${gitlab_port}:9001"
       - "${gitlab_ssh_port}:22"
3. modify file `${DOCKER_INSTALL}/gitlab/config/gitlab.rb`

       external_url 'http://${gitlab_host}:${gitlab_port}'
       gitlab_rails['gitlab_shell_ssh_port'] = ${gitlab_ssh_port}

       gitlab_rails['gitlab_email_from'] = '${gitlab_email_from}'
       gitlab_rails['gitlab_email_reply_to'] = '${gitlab_email_reply_to}'
       gitlab_rails['smtp_enable'] = ${smtp_enable}
       gitlab_rails['smtp_address'] = "${smtp_address}"
       gitlab_rails['smtp_port'] = ${smtp_port}
       gitlab_rails['smtp_user_name'] = "${smtp_user_name}"
       gitlab_rails['smtp_password'] = "${smtp_password}"
       gitlab_rails['smtp_domain'] = "${smtp_domain}"
       gitlab_rails['smtp_authentication'] = "${smtp_authentication}"
       gitlab_rails['smtp_enable_starttls_auto'] = ${smtp_enable_starttls_auto}
       gitlab_rails['smtp_tls'] = ${smtp_tls}
3. run it

       cd ${DOCKER_INSTALL}/gitlab
       docker-compose up -d
4. visit gitlab via `http://ip:${gitlab_port}`
5. visit gitlab with ssh via `ssh://git@ip:${gitlab_ssh_port}/xx/xx.git`