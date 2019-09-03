[![](https://images.microbadger.com/badges/version/neomediatech/rspamd-honey-alpine.svg)](https://microbadger.com/images/neomediatech/rspamd-honey-alpine)
[![](https://images.microbadger.com/badges/image/neomediatech/rspamd-honey-alpine.svg)](https://microbadger.com/images/neomediatech/rspamd-honey-alpine)
![](https://img.shields.io/github/last-commit/Neomediatech/rspamd-honey-docker-alpine.svg?style=plastic)
![](https://img.shields.io/github/repo-size/Neomediatech/rspamd-honey-docker-alpine.svg?style=plastic)

# rspamd-honey-docker-alpine
Dockerized version of rspamd as honeypot service, based on Alpine Linux

## Usage
You can run this container with this command:  
`docker run -d --name rspamd-honey-alpine neomediatech/rspamd-honey-alpine`  

Logs are written inside the container, in /var/log/rspamd/, and on stdout. You can see realtime logs running this command:  
`docker logs -f rspamd-honey-alpine`  
`CTRL c` to stop seeing logs.  

If you want to map logs outside the container you can add:  
`-v /folder/path/on-host/logs/:/var/log/rspamd/`  
Where "/folder/path/on-host/logs/" is a folder inside your host. You have to create the host folder manually.  

You can run it on a compose file like this:  

```
version: '3'  

services:  
  rspamd:  
    image: neomediatech/rspamd-honey-alpine:latest  
    hostname: rspamd-honey  
```
Save on a file and then run:  
`docker stack deploy -c /your-docker-compose-file-just-created.yml rspamd-honey`

If you want to map logs outside the container you can add:  
```
    volumes:
      - /folder/path/on-host/logs/:/var/log/rspamd/
```
Where "/folder/path/on-host/logs/" is a folder inside your host. You have to create the host folder manually.

Save on a file and then run:  
`docker stack deploy -c /your-docker-compose-file-just-created.yml rspamd-honey`  
