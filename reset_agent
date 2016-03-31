#!/bin/sh

DOCKER_CMD=$(docker inspect -f "{{.Config.Cmd}}" rancher-agent-bootstrap | sed 's/[\[{}]//g' | sed 's/\]//g')
AGENT_IMAGE=$(docker inspect -f "{{.Config.Image}}" rancher-agent-bootstrap)
# http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html
HOST_IP=$(wget -qO- http://169.254.169.254/latest/meta-data/public-ipv4)

docker run -d -e CATTLE_AGENT_IP=$HOST_IP \
    --privileged \
    -v /var/run/docker.sock:/var/run/docker.sock \
    $AGENT_IMAGE \
    $DOCKER_CMD
