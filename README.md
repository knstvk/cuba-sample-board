# cuba-sample-board
Cuba Platform project example for Nginx proxy

The application was configured in the Studio: 

    Project Properties - Edit - Advanced - Modules prefix: board
    
CUBA application is accessible at http://localhost/

nginx.conf part:
```
location /board {
    proxy_set_header X-Forwarded-Host $host;
    proxy_set_header X-Forwarded-Server $host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_read_timeout     3600;
    proxy_connect_timeout  240;
    proxy_set_header Host $host;
    proxy_set_header X-RealIP $remote_addr;

    proxy_pass http://127.0.0.1:8080/board;
    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
}
```
test
