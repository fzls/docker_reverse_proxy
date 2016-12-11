# 使用说明
在reverse-proxy.conf中定义所需要反向代理的服务器即可
> e.g.
> server
{
    listen 80;
    server_name pickup.moec.me web.moec.me www.moec.me;
    location / {
    proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass http://127.0.0.1:666;
    }
}

> server
{
    listen 80;
    server_name api.moec.me;
    location / {
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass http://127.0.0.1:2333;
    }
}
