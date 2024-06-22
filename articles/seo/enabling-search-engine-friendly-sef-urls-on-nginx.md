<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Nginx / Display title: Habilitando localizadores uniformes de recursos (URLs) amigáveis para mecanismos de buscas (SEFs) no Nginx -->

**Search engine friendly (SEF)**, **human-readable** or
<a href="https://en.wikipedia.org/wiki/Clean_URL" class="extiw"
title="wikipedia:Clean URL">clean URLs</a> are URLs that make sense to
both humans and search engines because they explain the path to the
particular page they point to. Since version 1.5, Joomla! is capable of
creating and parsing URLs in any format, including SEF URLs. This does
not depend on URL rewriting executed by the web server, so it works even
if Joomla! runs a server other than Apache with the mod_rewrite module.
The SEF URLs follow a certain fixed pattern, but the user can define a
short descriptive text (alias)
for each segment of the URL.

Internally, the local part of a SEF URL (the part after the domain name)
is called a *route*. Creating and processing SEF URLs is therefore
referred to as *routing*, and the relevant code is called a *router*.

Este artigo aborda localizadores uniformes de recursos (URLs) amigáveis
para mecanismos de buscas (SEFs) no popular servidor web de código
aberto <a href="http://nginx.net" class="external text" target="_blank"
rel="nofollow noreferrer noopener">Nginx</a>.

<img src="https://docs.joomla.org/images/5/53/Compat_icon_2_5.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 2.5" /> Desde o Joomla! 2.5, as localizadores
uniformes de recursos (URLs) amigáveis para mecanismos de buscas (SEFs)
básicas são habilitadas por padrão.
<img src="https://docs.joomla.org/images/c/c8/Compat_icon_1_5.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 1.5" /> Nas versões anteriores, você precisa
usar as configurações globais para habilitá-las. As instruções abaixo
ainda se aplicam se você quiser usar a reescrita mod_rewrite/URL do
Apache.

- Por favor, adicione o próximo código à configuração do seu servidor
  (vhost) no arquivo *nginx.conf*:
       # Support Clean (aka Search Engine Friendly) URLs
       location / {
          try_files $uri $uri/ /index.php?$args;
       }

- Se o acima não funcionar, adicione o próximo código à configuração do
  seu servidor no arquivo *nginx.conf*: (Isso funcionou com o nginx
  1.4.6 no Ubuntu.)
    server {
      ....
      location / {
         expires 1d;

         # Enable joomla SEF URL's inside Nginx
         try_files $uri $uri/ /index.php?$args;
      }
      ....
    }

- Inicie uma sessão no seu back-end e abra as configurações globais
- Ative a opção **localizadores uniformes de recursos (URLs) amigáveis
  para mecanismos de pesquisas (SEFs)** e *salve*. Esta opção converte
  os localizadores uniformes de recursos (URLs) do formato nativo do
  Joomla! para o formato amigável para mecanismos de pesquisas (SEF).
  Verifique se seu site funciona corretamente. Seus localizadores
  uniformes de recursos (URLs) agora devem se parecer com
  `http://www.example.com/index.php/the-­news/1-­latest­-news/1­-welcome­-to­-joomla`.
  Se o seu site não funcionar corretamente, consulte [Problemas comuns
  ao habilitar localizadores uniformes de recursos (URLs) amigáveis para
  mecanismos de pesquisas
  (SEFs)](https://docs.joomla.org/Common_problems_when_enabling_Search_Engine_Friendly_(SEF)_URLs/pt-br "Common problems when enabling Search Engine Friendly (SEF) URLs/pt-br")
- Habilite a opção **Usar a reescrita mod_rewrite/URL doApache** e
  *salve*. Esta opção usa a função *mod_rewrite* do Apache para eliminar
  a parte "index.php" dos localizadores uniformes de recursos (URLs)
  Verifique se seu site funciona corretamente. Seus localizadores
  uniformes de recursos (URLs) agora devem se parecer com
  `http://www.example.com/the-­news/1­-latest-­news/1-­welcome-­to­-joomla`.
  Se esta opção causar erros, consulte [Como verificar se o mod de
  reescrita está habilitado no seu
  servidor](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server/pt-br "How to check if mod rewrite is enabled on your server/pt-br").
  Se não estiver habilitado e você tiver acesso ao arquivo
  `apache/conf/httpd.conf`, abra esse arquivo e verifique se a linha
  `LoadModule rewrite_module modules/mod_rewrite.so` está descomentada.
  Se necessário, descomente a linha e reinicie o servidor web Apache.
  Se o *mod_rewrite* não puder ser habilitado, deixe esta opção
  desativada. Não importa se você deixar o arquivo `.htaccess`
  renomeado.
- *Se você achar que isso é necessário*, habilite **Adicionar sufixo aos
  localizadores uniformes de recursos (URLs)** e *salve*. Esta opção
  adiciona `.html` ao final dos localizadores uniformes de recursos
  (URLs). Existem opiniões diferentes sobre se isso é necessário ou
  mesmo útil. Os mecanismos de pesquisa parecem não se importar se seus
  localizadores uniformes de recursos (URLs) terminam em `.html` ou não.
- Abra o gerenciador de plugins e habilite o **Sistema - plugin SEF**.
  Este plugin adiciona suporte aos localizadores uniformes de recursos
  (URLs) amigáveis para mecanismos de buscas (SEFs) para links em seus
  artigos Joomla. Ele opera diretamente na HTML e não requer uma tag
  especial.
