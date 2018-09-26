This is single hostmachine of Consul and git2consl. not for Cluster
consul:
##### CONSUL SETUP
### CHecking my IP address of hostmachine
```bash
 - # ip -o -4 addr list|grep enp0s3| head -n1 | awk '{print $4}' | cut -d/ -f1
```
## To run single container of consul with single host. It will bind with your hostmachine's IP. Running container from dockerhub
```bash
 - # docker run -d --net=host --name=consul consul:1.0.2
```

## Checking default port status for UI
```bash
 - # netstat -tulpn |grep 8500
```

## Verifying container details
```bash
 - # docker inspect consul

## Veryfying single Consul UI
```bash
 - URL: http://<HOST-IP>:8500
```


git2consul:
##### original image: https://github.com/Cimpress-MCP/docker-git2consul
****************** GIT2CONSUL SETUP ******************
## The Docker file
```bash
 - # cd git2consul_consul
 - # docker build -t amitrepo/git2consul:0.12.13 .
```

## Create mount directory to access config.json file. Or use Volume data. OR upload config file in Container.
```bash
 - # mkdir /tmp/mydata-git2consul.d
 - # cp config.json /tmp/mydata-git2consul.d/config.json
```

## Run container from the gi2consul image
```bash
 - # docker run -d --name git2consul -v /tmp/mydata-git2consul.d:/etc/git2consul.d amitrepo/git2consul:0.12.13 --endpoint 172.18.46.14 --port 8500 --config-file /etc/git2consul.d/config.json

```
## Check running containers
```bash
 - # docker ps
```

##Check Key and Values for lmd service:
##http://172.18.46.14:8500/ui/#/dc1/kv/glt-project/glt-qa/lmd-service/

NOTE:
 - Create public and private key afterthan updaate in git to access it. OR use existing private key.
 - Restart git2consul, if any updates in key value on repo.
