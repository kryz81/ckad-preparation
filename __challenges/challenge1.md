**Create persistent volume**

1. name: log-volume
2. storage class: manual
3. access mode: read/write
4. size: 1Gi
5. mounted on host: /mnt/nginx

**Create persistent volume claim**

1. name: log-claim
2. request: 200Mi
3. Bind to the "log-volume" volume

**Create pod**

1. name: logger
2. image: nginx-alpine
3. Mount volume here: /var/www/nginx
