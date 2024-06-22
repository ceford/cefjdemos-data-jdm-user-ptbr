<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs / Display title: Ativando localizadores uniformes de recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs) -->

**Amigável para os mecanismos de pesquisas (SEF)**, **legível por
humanos** ou
<a href="https://en.wikipedia.org/wiki/pt:Slug_(programa%C3%A7%C3%A3o)"
class="extiw" title="wikipedia:pt:Slug (programação)">localizadores
uniformes de recursos (URLs) limpos</a> são localizadores uniformes de
recursos (URLs) que fazem sentido tanto para humanos quanto para
mecanismos de pesquisa porque explicam o caminho para a página
específica para a qual apontam. Desde a versão 1.5, Joomla! é capaz de
criar e analisar localizadores uniformes de recursos (URLs) em qualquer
formato, incluindo localizadores uniformes de recursos (URLs) amigáveis
para mecanismos de pesquisas (SEFs). Isso não depende da reescrita de
localizadores uniformes de recursos (URLs) executada pelo servidor web,
então funciona mesmo que o Joomla! seja executado um servidor diferente
do Apache com o módulo mod_rewrite. Os localizadores uniformes de
recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs) seguem um
certo padrão fixo, mas o usuário pode definir um  texto descritivo curto
(alias) para cada
segmento dos localizadores uniformes de recursos (URLs).

Internamente, a parte local de um localizador uniforme de recursos (URL)
amigável para mecanismos de pesquisas (SEF) (a parte após o nome do
domínio) é chamada de **rota**. A criação e processamento dos
localizadores uniformes de recursos (URLs) amigáveis para mecanismos de
pesquisas (SEFs) é, portanto, chamado de **roteamento**, e o código
relevante é chamado de **roteador**.

O procedimento para habilitar URLs amigáveis para mecanismos de pesquisa
difere dependendo do servidor web que você estiver usando. Se você
estiver usando hospedagem compartilhada, provavelmente é o Apache. Peça
mais informações ao seu provedor de hospedagem se não tiver certeza.

Apenas os servidores web mais populares foram incluídos nesta página.
Visite [Ativando localizadores uniformes de recursos (URLs) amigáveis
para mecanismos de pesquisas (SEFs) no
IIS](https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs_on_IIS "Enabling Search Engine Friendly (SEF) URLs on IIS")
(apenas em inglês) e [Categoria:Localizadores uniformes de recursos
(URLs) amigáveis para mecanismos de pesquisas
(SEFs)](https://docs.joomla.org/Category:Search_Engine_Friendly_URLs/pt-br "Category:Search Engine Friendly URLs/pt-br")
para mais artigos.

## Apache

## Verifique se o .htaccess está habilitado

Verifique se o arquivo de configuração do Apache permite substituições
do .htaccess. Você deve certificar-se de que as substituições estão
habilitadas ou o arquivo .htaccess em seu diretório raiz do Joomla! será
ignorado ou causará um erro. Na seção do seu arquivo de configuração do
host virtual ou no arquivo de configuração principal (`httpd.conf`),
você deve ter algo semelhante ao exemplo abaixo, habilitando
substituições:

```bash
<Directory "/home/user/public_html">
  AllowOverride All
</Directory>

<Directory "/path/to/htdocs">
  AllowOverride All Options=[an option],[an option],...
</Directory>
```

Existem outras maneiras de testar se o `.htaccess` está habilitado se
você não tiver acesso aos arquivos de configuração do seu site. Consulte
o <a href="http://httpd.apache.org/docs/current/howto/htaccess.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">.htaccess tutorial</a> encontrado no
site da
<a href="http://www.apache.org/" class="external text" target="_blank"
rel="nofollow noreferrer noopener">Fundação do software Apache</a> para
obter informações adicionais .

## Passo a passo

Estas são instruções passo a passo. Por favor, siga-os na ordem em que
são apresentados aqui. Se um passo falhar, **não** continue até que você
tenha resolvido o problema.

1.  Renomeie o arquivo `"htaccess.txt"` na pasta base do seu Joomla!
    para `".htaccess"`.

2.  *Esse passo pode não ser necessário*: Abra o `.htaccess` em um
    editor de texto. Descomente `RewriteBase /` (remova o primeiro
    caractere, \#). Se o Joomla estiver instalado em sua própria pasta,
    digite o nome da pasta do Joomla após a barra. Por exemplo,
    `RewriteBase /sua_pasta_do_joomla`.

3.  Inicie uma sessão no seu back-end e abra as configurações globais.

4.  Habilite a opção **Usar a reescrita do mod_rewrite/URL do Apache** e
    *salve*. Esta opção usa a função *mod_rewrite* do Apache para
    eliminar a parte "index.php" do URL.

    Verifique se o seu site funciona corretamente. Seus URLs agora devem
    ter a seguinte aparência:

        http://www.example.com/the-news/1-latest-news/1-welcome-to-joomla

    Se esta opção causar erros, consulte [Como verificar se o mod de
    reescrita está habilitado no seu
    servidor](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server "Special:MyLanguage/How to check if mod rewrite is enabled on your server").

    - Se não estiver habilitado e você tiver acesso ao arquivo
      `apache/conf/httpd.conf`, abra esse arquivo e verifique se a linha
      `LoadModule rewrite_module modules/mod_rewrite.so` está
      descomentada. Se necessário, descomente a linha e reinicie o
      servidor web Apache.
    - Se o *mod_rewrite* não puder ser habilitado, deixe esta opção
      desativada. Não importa se você deixar o arquivo `.htaccess`
      renomeado.

5.  *Se achar necessário*, habilite a **adição de sufixo aos URLs** e
    *salve*. Esta opção adiciona `.html` ao final dos URLs. Existem
    opiniões diferentes sobre se isso é necessário ou mesmo útil. Os
    mecanismos de pesquisa parecem não se importar se seus URLs terminam
    em `.html` ou não.

6.  Abra o gerenciador de plugins e habilite **Sistema - plugin SEF**.
    Este plugin adiciona suporte SEF para links em seus artigos do
    Joomla. Ele opera diretamente no HTML e não requer uma tag especial.

## Hiawatha

Use a seguinte regra do UrlToolkit para habilitar URLs limpos no
servidor web Hiawatha:

    UrlToolkit {
        ToolkitID = joomla
        Match base64_encode.*\(.*\) DenyAccess
        Match (<|%3C).*script.*(>|%3E) DenyAccess
        Match GLOBALS(=|\[|\%[0-9A-Z]{0,2}) DenyAccess
        Match _REQUEST(=|\[|\%[0-9A-Z]{0,2}) DenyAccess
        RequestURI exists Return
        Match /index.php Return
        Match ^/component/ Skip 2
        Match ^(/|\.php|\.html|\.htm|\.feed|\.pdf|\.raw|/[^.]*)$ Skip 1
        Skip 1
        Match .* Rewrite /index.php
    }

Habilite uma regra do UrlToolkit para um host virtual por meio da
configuração do UseToolkit:

    VirtualHost {
        ...
        UseToolkit = joomla
    }

## IIS 7

Se você tiver um servidor executando o IIS 7 e o PHP, poderá aproveitar
a própria reescrita de URL interna do IIS usando um arquivo web.config
semelhante ao listado abaixo.

Você pode criar o arquivo sozinho ou usar a interface gráfica do usuário
no gerenciador do IIS7. Você pode importar regras do .htaccess usando o
assistente da interface gráfica do usuário.

Esta funcionalidade depende da presença do **Módulo de reescrita de URL
do IIS**, que não vem com o Windows. É um download gratuito e um produto
da Microsoft.

### Interface gráfica do usuário

Se o módulo de reescrita de URL do IIS estiver instalado, o gerenciador
de seu site terá uma ferramenta para "reescrita de URL", visível na
exibição do gerenciador dos IIS dos módulos para IIS configuráveis do
seu site. A interface é amplamente auto-explicativa. Expressões
regulares, curingas ou correspondências exatas são todas suportadas.

Na configuração do Joomla, ative o mod_rewrite do SEF e do Apache, em
seguida, crie uma regra na reescrita de URL do IIS:

Pattern field: **^(\[^/\]+)/?\$**

Ignore case **ON**

Action type: **Rewrite**

Rewrite URL: **index.php/**

### web.config

Isso foi testado no Joomla 1.5 com IIS 7 no Windows Server 2008 sem
problemas até agora. Para obter mais informações sobre como converter
.htaccess para web.config, confira <a
href="http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/</a>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <clear />
                <rule name="Common Exploit Blocking" stopProcessing="true">
                    <match url="^(.*)$" />
                    <conditions logicalGrouping="MatchAny">
                        <add input="{QUERY_STRING}" pattern="mosConfig_[a-zA-Z_]{1,21}(=|\%3D)" />
                        <add input="{QUERY_STRING}" pattern="base64_encode.*\(.*\)" />
                        <add input="{QUERY_STRING}" pattern="(\&lt;|%3C).*script.*(\>|%3E)" />
                        <add input="{QUERY_STRING}" pattern="GLOBALS(=|\[|\%[0-9A-Z]{0,2})" />
                        <add input="{QUERY_STRING}" pattern="_REQUEST(=|\[|\%[0-9A-Z]{0,2})" />
                    </conditions>
                    <action type="Redirect" url="index.php" appendQueryString="false" redirectType="SeeOther" />
                </rule>
                <rule name="Joomla Search Rule" stopProcessing="true">
                    <match url="(.*)" ignoreCase="true" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{URL}" pattern="^/search.php" ignoreCase="true" />
                    </conditions>
                    <action type="Rewrite" url="/index.php?option=com_content&amp;view=article&amp;id=4" />
                </rule>
                <rule name="Joomla Main Rewrite Rule" stopProcessing="true">
                    <match url="(.*)" ignoreCase="true" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{URL}" pattern="(/[^.]*|\.(php|html?|feed|pdf|raw))$" />
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="index.php/" />
                </rule>
            </rules>
        </rewrite>
        <caching>
            <profiles>
                <add extension=".php" policy="DisableCache" kernelCachePolicy="DisableCache" />
            </profiles>
        </caching>
    </system.webServer>
</configuration>
```

## Nginx

- Por favor, adicione o próximo código à configuração do seu servidor
  (vhost) no arquivo *nginx.conf*:

  ```
       # Support Clean (aka Search Engine Friendly) URLs
       location / {
          try_files $uri $uri/ /index.php?$args;
       }
```

- Se o acima não funcionar, adicione o próximo código à configuração do
  seu servidor no arquivo *nginx.conf*: (Isso funcionou com o nginx
  1.4.6 no Ubuntu.)

```
    server {
      ....
      location / {
         expires 1d;

         # Enable joomla SEF URL's inside Nginx
         try_files $uri $uri/ /index.php?$args;
      }
      ....
    }
```

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
