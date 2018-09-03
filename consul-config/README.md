# consul
TO update Consul KV from Git2cosnul
this is git2consul-config-consul config file for Consul KV

# Docker

## Docker - Consul latest 1.2.2
- # docker pull consul
- # docker run -d --restart always -p 8300:8300 -p 8301:8301 -p 8301:8301/udp -p 8302:8302/udp -p 8302:8302 -p 8400:8400 -p 8500:8500 consul
- # lsof -i :8500
- # URL: http://172.18.46.14:8500
