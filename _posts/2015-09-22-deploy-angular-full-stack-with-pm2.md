---
layout: post
title: Deploy Angular-FullStack with PM2 on Ubuntu
---

Deploy Angular-Fullstack or Nodejs project run with Grunt/Gulp Task

## Install Nginx 

```sh
sudo apt-get install nginx
```

## Install PM2

```sh
npm install -g  pm2
```

## Start Angular-Fullstack Grunt task with PM2

```sh
pm2 start $(which grunt) serve:dist # production mode
```

```
Output:
┌──────────┬────┬──────┬──────┬────────┬───────────┬────────┬────────────┬──────────┐
│ App name │ id │ mode │ PID  │ status │ restarted │ uptime │     memory │ watching │
├──────────┼────┼──────┼──────┼────────┼───────────┼────────┼────────────┼──────────┤
│ app_name │ 0  │ fork │ 5871 │ online │         0 │ 0s     │ 9.012 MB   │ disabled │
└──────────┴────┴──────┴──────┴────────┴───────────┴────────┴────────────┴──────────┘
```

Pm2 will start Angular-Fulltack App on port `9000`, see `http://localhost:9000`

## Set Up Reverse Proxy Server

<img src="https://assets.digitalocean.com/articles/nodejs/node_diagram.png" />

Open the default server block configuration file for editing:

```sh
sudo vi /etc/nginx/sites-available/default
```

Delete everything in the file and insert the following configuration. 
Be sure to substitute your own domain name for the server_name directive 
(or IP address if you don't have a domain set up), and the app server private 
IP address for the `APP_PRIVATE_IP_ADDRESS`. Additionally, change the port (`9000`) 
if your application is set to listen on a different port:

```
server {
    listen 80;

    server_name example.com;

    location / {
        proxy_pass http://localhost:9000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

On the web server, restart Nginx:
```sh
sudo service nginx restart
```
