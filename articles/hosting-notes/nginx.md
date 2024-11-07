<!-- Filename: Nginx / Display title: Nginx -->

<a href="http://nginx.org/"
rel="nofollow noreferrer noopener">Nginx</a> é um servidor Web leve
que alimenta
<a href="https://en.wikipedia.org/wiki/Nginx"
rel="nofollow noreferrer noopener">cerca de 33%</a> dos servidores Web
em todos os domínios. A menos que você tenha requisitos específicos que
exijam um servidor Web pesado como o Apache, é muito melhor usar
o Nginx.

Abaixo estão as instruções sobre como fazer o Joomla! funcionar com o <a
href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/"
rel="nofollow noreferrer noopener">Exemplo de PHP FastCGI</a>.
 -->

## Instalar o Nginx

Para Ubuntu, execute *aptitude install Nginx*. Para outras distribuições, execute o gerenciador de pacotes correspondente ou consulte a <a href="https://www.nginx.com/resources/wiki/start/topics/tutorials/install/" rel="nofollow noreferrer noopener">página de instalação do Nginx</a>.

## Instalar PHP FastCGI

Para Ubuntu, leia o <a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">Exemplo de PHP FastCGI</a>.

Para Gentoo, o PHP será executado como um serviço FastCGI (FPM), então o servidor Nginx irá executar o PHP como um processo separado:

    # echo "dev-lang/php gd gd2 curl simplexml tokenizer dom tidy sqlite xml fpm cgi" >> /etc/portage/package.use
    # emerge php

As configurações padrão do PHP-FPM são boas para a maioria dos servidores. Para configurações especiais, visite o
<a href="http://php.net/manual/en/install.fpm.php" rel="nofollow noreferrer noopener">site PHP FPM</a>.

## Configurar Nginx

Os arquivos de configuração do Nginx estão localizados em:

- `/etc/nginx/sites-available/` no Ubuntu (para sites que rodam nessa
  instância do Nginx)
- `/etc/nginx/nginx.conf` no Gentoo e Raspbian (Debian otimizado para
  Raspberry Pi)

Aqui está um exemplo de arquivo de configuração Nginx, *joomla.conf*, que você pode
reutilizar em todos os seus sites habilitados para Nginx.

```nginx
server {
  listen 80;
    server_name SEU_DOMÍNIO;
    server_name_in_redirect off;

    access_log /var/log/nginx/localhost.access_log;
    error_log /var/log/nginx/localhost.error_log info;

    root CAMINHO_NO_SERVIDOR;
    index index.php index.html index.htm default.html default.htm;
    # Suporte a URLs limpas (também conhecidas como amigáveis para SEO)
    location / {
        try_files $uri $uri/ /index.php?$args;
    }

    # adiciona cabeçalho global x-content-type-options
    add_header X-Content-Type-Options nosniff;

    # nega a execução de scripts dentro de diretórios graváveis
    location ~* /(images|cache|media|logs|tmp)/.*\.(php|pl|py|jsp|asp|sh|cgi)$ {
        return 403;
        error_page 403 /403_error.html;
    }

    location ~ \.php$ {
      fastcgi_pass  127.0.0.1:9000;
      fastcgi_index index.php;
      include fastcgi_params;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
      include /etc/nginx/fastcgi.conf;
    }

    # cache de arquivos
    location ~* \.(ico|pdf|flv)$ {
        expires 1y;
    }

    location ~* \.(js|css|png|jpg|jpeg|gif|swf|xml|txt)$ {
        expires 14d;
    }
}
```

Preste atenção a algumas coisas:

1. O parâmetro *fastcgi_pass* está configurado como *127.0.0.1:9000*,
   correspondente à porta que o FPM está configurado para escutar. Isso
   significa que você pode executar os processos PHP em servidores separados. No Gentoo,
   você pode encontrar esta configuração no arquivo
   */etc/php/fpm-php5.3/php-fpm.conf/*.
2. Não se esqueça de substituir SEU_DOMÍNIO e CAMINHO_NO_SERVIDOR conforme mencionado acima,
   dependendo do seu domínio e do caminho do Joomla no seu servidor.

## Suporte a GZip

Se você precisar de suporte para compressão GZip, adicione a seguinte seção à seção *http* do arquivo de configuração principal do Nginx:

```nginx
gzip on;
gzip_http_version 1.1;
gzip_comp_level 6;
gzip_min_length 1100;
gzip_buffers 4 8k;
gzip_types text/plain application/xhtml+xml text/css application/xml application/xml+rss text/javascript application/javascript application/x-javascript;
gzip_proxied any;
gzip_disable "MSIE [1-6]\.";
```

## Fontes

- <a href="https://wiki.gentoo.org/wiki/Nginx"
rel="nofollow noreferrer noopener">Nginx no Gentoo</a>
- <a href="https://kevinworthington.com/nginx-for-windows/"
  rel="nofollow noreferrer noopener">Nginx para Windows</a>
- <a
  href="https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview"
  rel="nofollow noreferrer noopener">Nginx no Ubuntu</a>
- <a
  href="https://www.debianadmin.com/howto-install-nginx-webserver-in-debian.html"
  rel="nofollow noreferrer noopener">Nginx no Debian</a>
- <a href="https://www.php.net/manual/en/install.fpm.php"
  rel="nofollow noreferrer noopener">Instalação e configuração do PHP-FPM</a>
- <a
  href="https://docs.nginx.com/nginx/admin-guide/web-server/compression/"
  rel="nofollow noreferrer noopener">Compressão e Descompressão</a>
- <a href="https://www.nginx.com/blog/creating-nginx-rewrite-rules/"
  rel="nofollow noreferrer noopener">Criando Regras de Rewrite no NGINX</a>
- <a href="http://nginx.org/en/docs/http/request_processing.html"
  rel="nofollow noreferrer noopener">Como o Nginx processa uma requisição</a>

*Traduzido por openai.com*

