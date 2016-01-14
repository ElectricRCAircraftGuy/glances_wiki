# Apache configuration

    RewriteEngine on
    RewriteCond %{HTTP_REFERER} ^https?://[^/]+/glances
    RewriteCond %{REQUEST_URI} !^/glances
    RewriteCond %{THE_REQUEST} ^GET
    RewriteRule ^/(.*) /glances/$1 [QSA,R]
    ProxyPass /glances/ http://localhost:61208/
    ProxyPassReverse /glances/ http://localhost:61208/
    Redirect permanent /glances http://host/glances/

# Nginx

    location / {


      if ($http_referer ~ "^https?://[^/]+/glances"){


        rewrite ^/(.*) /glances/$1 redirect;


      }


    }


    


    location /glances/ {


      rewrite /glances/(.*) /$1 break;


      proxy_pass http://localhost:61208/;


      proxy_set_header Host $http_host;


      proxy_set_header X-Real-IP $remote_addr;


      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;


      proxy_set_header X-Forwarded-Proto $scheme;


    }

