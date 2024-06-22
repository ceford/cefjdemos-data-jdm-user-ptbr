<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Apache / Display title: Habilitando URLs amigáveis para mecanismos de pesquisas (SEF) no Apache -->


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

Este artigo aborda URLs SEF no popular servidor web de código aberto
Apache. A implementação de URL SEF também é possível no servidor web IIS
da Microsoft, consulte [Habilitando URLs amigáveis para mecanismos de
pesquisas (SEF) no
IIS](https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs_on_IIS "Special:MyLanguage/Enabling Search Engine Friendly (SEF) URLs on IIS").

Desde o Joomla!
<img src="https://docs.joomla.org/images/d/da/Compat_icon_1_6.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 1.6" />, urls SEF básicas são habilitadas por
padrão. Nas versões anteriores, você precisa usar as configurações
globais para habilitá-los. As instruções abaixo ainda se aplicam se você
quiser usar a reescrita do mod_rewrite/URL do Apache.

## Verifique se o .htaccess está habilitado

Verifique se o arquivo de configuração do Apache permite substituições
do .htaccess. Você deve certificar-se de que as substituições estão
habilitadas ou o arquivo .htaccess em seu diretório raiz do Joomla! será
ignorado ou causará um erro. Na seção do seu arquivo de configuração do
host virtual ou no arquivo de configuração principal (`httpd.conf`),
você deve ter algo semelhante ao exemplo abaixo, habilitando
substituições:

      AllowOverride All



      AllowOverride All Options=[an option],[an option],...

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
