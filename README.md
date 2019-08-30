This dockerfile uses NGINX proxy and the letsencrypt companion to automaticaly provide HTTPS to containers

What this project does:
redirect urls to designated containers and provides https to encrypt traffic going to containers

How it works:
The example container provides all of the options required to connect your container to the proxy.
To add a container to the proxy add these options to your service:
    
    environment:
      - VIRTUAL_HOST=[example.website.com]
      - LETSENCRYPT_HOST=[example.website.com]
      - LETSENCRYPT_EMAIL=[example@email.com]
    depends_on:
      - letsencrypt
      - proxy
    
Your host computer must be accessible from ports 80 and 443 for letsencrypt to properly sign the SSL certs
