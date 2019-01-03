---
title: nginx
date: 2018-03-23 14:01:36
tags: nginx
categories: web
---
- [代理](#代理)
- [nginx](#nginx)
- [config](#config)

<!-- more -->


# 代理
> 正向代理代理客户端，反向代理代理服务器

# nginx
- one master process   
  (read and evaluate configuration  and maintain worker process)
- serval worker processes

# config
- /etc/nginx/nginx.conf
  
```
include /etc/nginx/conf.d/*.conf;
include /etc/nginx/sites-enabled/*;

```

```
main
    events
    {

    }
    http{        
        server{
            listen localhost:8080;
            location / {
                root /data/www
            }

            location /images{
                root /data/images
            }
        }
        server{
            listen localhost:8081;
            location / {
                ... ...
            }
        }

    }
```

- directive
    - simple directive
        ```
        include /etc/nginx/conf.d/*.conf;
        ```
    - context   
        ```
        server{
            listen localhost:80;
            ... ...
        }   
        ```

    



