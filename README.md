# LoadBalance-nginx
upstream balance {
least_conn;
server 192.168.0.197:80;
server 192.168.0.198:80;
server 192.168.0.196:80;
}

server {
        listen 80;
        root /etc/html;
        server_name 192.168.0.196;

location / {
        proxy_pass http://balance/;
}
}
