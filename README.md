# Gitlab Runner

### Запуск раннера
```
docker run -d --name gitlab-runner --restart always \
  -v /srv/gitlab-runner/config:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:alpine
```

### Регистрация раннера
```
docker run --rm -it \
    -v /srv/gitlab-runner/config:/etc/gitlab-runner \
    gitlab/gitlab-runner:alpine register
```

### Изменение конфига
#### Шаг 1
Заходим в режим редактирования конфига через        
`nano /srv/gitlab-runner/config/config.toml`        
или     
`vim /srv/gitlab-runner/config/config.toml`

#### Шаг 2 
Меняем      
`volumes = ["/cache"]` на       
```
volumes = ["/var/run/docker.sock:/var/run/docker.sock", "/cache"]
```