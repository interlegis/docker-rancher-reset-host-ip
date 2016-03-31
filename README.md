# docker-rancher-reset-host-ip
Updates rancher host IP on EC2 instance
## docker run command
`docker run --rm  -v /var/run/docker.sock:/var/run/docker.sock -it reset_agent`
## docker-compose
```
update-host-ip:
  log_driver: ''
  labels:
    io.rancher.scheduler.global: 'true'
    io.rancher.container.pull_image: always
    io.rancher.container.start_once: 'true'
  tty: true
  log_opt: {}
  image: getapp/rancher-reset-host-ip
  volumes:
  - /var/run/docker.sock:/var/run/docker.sock
  stdin_open: true
```
