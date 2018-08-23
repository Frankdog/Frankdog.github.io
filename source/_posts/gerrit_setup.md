---
title: gerrit setup
date: 2018-08-23 10:09:28
tags: docker gerrit
---

# docker + nginx + gerrit 

## install gerrit
```bash
sudo docker pull openfrontier/gerrit
```

## run gerrit
```bash
mkdir $PWD/gerrit_volume
sudo docker run \
    --name gerrit \
    -v $PWD/gerrit_volume:/var/gerrit/review_site \
    -p 8081:8080 -p 29418:29418 \
    -e AUTH_TYPE=HTTP \
    -d openfrontier/gerrit
```



## install nginx
```bash
sudo docker pull nginx
mkdir $PWD/nginx_volume
touch $PWD/nginx_volume/gerrit.conf

htpassword -c $PWD/nginx_volume/gerrit.passwd admin

echo 'server {
 #nginx proxy port 
 listen 8080;
 server_name localhost;
 location ^~ / {
   auth_basic "Restricted";
   auth_basic_user_file /etc/nginx/conf.d/gerrit.passwd;
   #gerrit service port
   proxy_pass        http://127.0.0.1:8081; 
   proxy_set_header  X-Forwarded-For $remote_addr;
   proxy_set_header  Host $host;
   }
}' > $PWD/nginx_volume/gerrit.conf

```

## run nginx
```bash
sudo docker --name nginx run -p 8080:8080 -v $PWD/nginx_volume/gerrit.conf:/etc/nginx/conf.d/gerrit.conf
-v $PWD/nginx_volume/gerrit.passwd:/etc/nginx/conf.d/gerrit.passwd
-d nginx
```


## visit gerrit web   
> http://localhost:8080/
