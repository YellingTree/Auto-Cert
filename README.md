This dockerfile allows you to run mulitple containers under the same ports by using NGINX as a proxy and the letsencrypt image to assign certs. 

The proxy will redirect incoming urls to designed containers while allowing all of them to run under the same port

    Example:
    example1.website.com points to service1
    example2.website.com points to service2

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
