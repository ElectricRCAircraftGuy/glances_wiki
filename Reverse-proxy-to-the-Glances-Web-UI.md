# Apache configuration

`
RewriteEngine on
RewriteCond %{HTTP_REFERER} ^https?://[^/]+/glances
RewriteCond %{REQUEST_URI} !^/glances
RewriteCond %{THE_REQUEST} ^GET
RewriteRule ^/(.*) /glances/$1 [QSA,R]

ProxyPass /glances/ http://localhost:61208/
ProxyPassReverse /glances/ http://localhost:61208/

Redirect permanent /glances http://host/glances/
`