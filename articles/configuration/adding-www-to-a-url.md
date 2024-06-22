<!-- Filename: Adding_www_to_a_url / Display title: Adicionando www à url -->

## Como faço para ter www como um prefixo em todos os meus sites Joomla!?

Adicione o seguinte para o seu arquivo `.htaccess`:

    RewriteEngine On
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]

Uma solução mais completa que resolve vários outros problemas de
canonização ao mesmo tempo:

    RewriteEngine On
    #
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.html?\ HTTP/
    RewriteRule ^(([^/]+/)*)index\.html?$ http://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{THE_REQUEST} !^POST
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.php\ HTTP/
    RewriteCond %{SERVER_PORT}>s ^(443>(s)|[0-9]+>s)$
    RewriteRule ^(([^/]+/)*)index\.php$ http%2://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]
