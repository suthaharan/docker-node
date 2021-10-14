# To setup basic nodejs app
```
$ cd app
$ npm init
$ npm install express
```

# To start docker, run

```
$ docker-compose up --build
```

# Ref notes on setting up multiple connections to node apps
```
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        server_name nodeserver;

        location / {
                proxy_http_version 1.1;
                proxy_cache_bypass $http_upgrade;

                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;

                proxy_pass http://localhost:5000;
        }
        
        location /server2 {
                proxy_http_version 1.1;
                proxy_cache_bypass $http_upgrade;

                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;

                proxy_pass http://localhost:8000;
        }
}
```

# Reference links

* Base NodeJS with nginx [https://ashwin9798.medium.com/nginx-with-docker-and-node-js-a-beginners-guide-434fe1216b6b]
* Additional steps for ref check [https://www.edureka.co/blog/docker-compose-containerizing-mean-stack-application/]