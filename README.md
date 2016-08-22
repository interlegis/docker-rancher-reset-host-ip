# docker-rancher-reset-host-ip
Updates rancher host IP when it changes.
## docker run command
`docker run --rm  -v /var/run/docker.sock:/var/run/docker.sock -it interlegis/rancher-reset-host-ip`
## docker-compose
```
update-host-ip:
  log_driver: ''
  net: host
  labels:
    io.rancher.scheduler.global: 'true'
    io.rancher.container.pull_image: always
    io.rancher.container.start_once: 'true'
  tty: true
  log_opt: {}
  image: interlegis/rancher-reset-host-ip
  volumes:
  - /var/run/docker.sock:/var/run/docker.sock
  stdin_open: true
```

## Remarks
The container used to add the host to Rancher must be named "rancher-agent-bootstrap"
