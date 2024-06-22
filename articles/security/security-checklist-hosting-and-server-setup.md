<!-- Filename: Security_Checklist/Hosting_and_Server_Setup / Display title: Lista de verificação de segurança/Hospedagem e configuração de servidor -->

<table class="navbox" data-cellspacing="0">

<tbody>
<tr class="odd">
<td><table class="nowraplinks navbox-inner" data-cellspacing="0">

<tbody>
<tr class="header">
<th colspan="2" class="navbox-title" scope="col">Security Checklist <img
src="https://docs.joomla.org/images/7/7b/Compat_icon_CMS.png"
decoding="async" data-file-width="87" data-file-height="17" width="87"
height="17" alt="Joomla CMS" /></th>
</tr>
&#10;<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-abovebelow"></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-list navbox-odd"><table
class="nowraplinks navbox-subgroup" data-cellspacing="0">

<tbody>
<tr class="header">
<th colspan="2" class="navbox-title" scope="col"><em>Articles in this
series</em></th>
</tr>
&#10;<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-list navbox-odd"><ul>
<li><a href="https://docs.joomla.org/Security_Checklist/Getting_Started"
title="Special:MyLanguage/Security Checklist/Getting Started">Primeiros
passos</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Hosting_and_Server_Setup"
title="Special:MyLanguage/Security Checklist/Hosting and Server Setup">Hospedagem
e configuração de servidor</a></li>
<li><a href="https://docs.joomla.org/Enabling_HTTPS_on_your_site"
title="Special:MyLanguage/Enabling HTTPS on your site">Habilitando o
HTTPS em seu site</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Where_can_you_learn_more_about_file_permissions%3F"
title="Special:MyLanguage/Security Checklist/Where can you learn more about file permissions?">Saiba
mais sobre permissões de arquivo</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Testing_and_Development"
title="Special:MyLanguage/Security Checklist/Testing and Development">Testes
e desenvolvimento</a></li>
<li><a href="https://docs.joomla.org/Security_Checklist/Joomla!_Setup"
title="Special:MyLanguage/Security Checklist/Joomla! Setup">Configuração
do Joomla!</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Administration">Administração
do site</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Recovery">Recuperação
de sites</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/You_have_been_hacked_or_defaced"
title="Special:MyLanguage/Security Checklist/You have been hacked or defaced">Você
foi hackeado ou adulterado</a></li>
</ul></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

## Escolher um provedor de hospedagem qualificado

### A decisão mais importante

Provavelmente nenhuma decisão é mais crítica para a segurança do site do
que a escolha de hosts e servidores. No entanto, devido à grande
variedade de opções e configurações de hospedagem, não é possível
fornecer uma lista completa para todas as situações. Verifique esta
<a href="https://resources.joomla.org/en/category/hosting-providers"
class="external text" target="_blank" rel="noreferrer noopener">lista de
hosts</a> que atendem aos requisitos de segurança de um site Joomla
típico. ( Perguntas
frequentes

### Riscos de servidores compartilhados

Se você está com um orçamento apertado e seu site não processa dados
altamente confidenciais, você provavelmente pode se virar com um
servidor compartilhado, mas você deve entender os riscos inevitáveis. A
maioria das dicas listadas abaixo são apropriadas para proteger sites em
ambientes de servidores compartilhados.

## Configurando o Apache

### Usar o .htaccess do Apache

*Consulte também  exemplos de
.htaccess*

Bloqueie tentativas de exploração típicas com arquivos locais
*.htaccess* do Apache. Essa opção não está ativada em todos os
servidores. Verifique com o seu host se tiver problemas. Usando o
*.htaccess*, você pode proteger diretórios confidenciais (como o
administrator) com senha, restringir (por endereço de protocolo de
Internet) o acesso a diretórios confidenciais e, dependendo da
configuração do seu servidor, você pode aumentar a segurança mudando
para o PHP7.

O Joomla vem com um arquivo  .htaccess
préconfigurado,
mas \*você\* precisa escolher usá-lo. O arquivo é chamado htaccess.txt.
Para usá-lo, renomeie-o para .htaccess e coloque-o na raiz do seu site
usando o protocolo de transferência de arquivo (FTP). Um ponto
importante a ser observado é que como o arquivo distribuído é chamado
htaccess.txt e o arquivo ao vivo em seu site é chamado .htaccess, o
arquivo que seu site realmente usa não é atualizado quando você atualiza
seu site para usar uma nova versão do Joomla. Você deve fazer as
alterações manualmente para usar a nova versão do arquivo.

Considere seguir o princípio de "privilégio mínimo" para executar o PHP
usando ferramentas como o PHPsuExec, o php_suexec ou o suPHP.
(Observação: esses são métodos avançados que exigem acordo e coordenação
com seu provedor de hospedagem. Essas opções são habilitadas ou
desabilitadas em todo o servidor e não são ajustáveis individualmente em
servidores compartilhados.)

Considere usar uma solução de filtragem do lado do servidor como o
mod_security do Apache - um ótimo ponto de partida é o OWASP ModSecurity
<a href="https://coreruleset.org/" class="external text" target="_blank"
rel="nofollow noreferrer noopener">CoreRuleSet</a>

### Executando o PHP como um módulo do Apache

Isso causa problemas de propriedade e, portanto, problemas de permissão
que levarão a problemas de segurança. É melhor selecionar uma
configuração de servidor/host que execute o php como um processo cgi
(como cgi-fcgi) junto com o uso do phpSuExec ou uma configuração
semelhante.

Os dois melhores tutoriais e explicações sobre permissões, propriedades
e suas relações são desta página oficial de documentação do Joomla:

-  Permissões de
  arquivo
-  Aviso de propriedade de
  arquivo

Tópicos específicos para ler seriam os dois seguintes:

-  Manual de permissões do
  Unix

E para informações sobre o phpSuExec e implementações semelhantes:

-  Usando o
  phpSuExec

### Usar o mod_security do Apache

Configure os filtros mod_security e mod_rewrite do Apache para bloquear
ataques ao PHP. Consulte
<a href="https://www.google.com/search?q=apache%20mod_security"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Pesquisa do Google para
mod_security</a> e
<a href="https://www.google.com/search?q=apache%20mod_rewrite"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Pesquisa do Google para
mod_rewrite</a>. (Observação: esses são métodos avançados que geralmente
exigem acordo e coordenação com seu provedor de hospedagem. Essas opções
são habilitadas ou desabilitadas em todo o servidor e não são ajustáveis
individualmente em servidores compartilhados.)

## Configurando o MySQL

### Proteger o banco de dados

Certifique-se de que as contas do MySQL estejam definidas com acesso
limitado. A instalação inicial do MySQL é insegura e uma configuração
cuidadosa é necessária. (Consulte os
<a href="http://dev.mysql.com/doc/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">manuais do MySQL</a>)
Nota: Este item se aplica somente àqueles que administram seus próprios
servidores, como servidores dedicados. Os usuários de servidores
compartilhados dependem de seu provedor de hospedagem para definir a
segurança adequada do banco de dados.)

## Configurando o PHP

### Entender como funciona o PHP

Entenda como trabalhar com o arquivo php.ini e como as configurações do
PHP são controladas. Estude a
<a href="http://us3.php.net/manual/en/ini.php#ini.list"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Lista oficial de diretivas do
php.ini</a> em
<a href="http://www.php.net" class="external free" target="_blank"
rel="nofollow noreferrer noopener">http://www.php.net</a>, e o bem
documentado php.ini padrão incluído em cada instalação do PHP.

### Usar o PHP7

As versões do PHP se tornaram obsoletas e algumas se tornaram obsoletas.
Alguns provedores de hospedagem ainda possuem várias disponíveis em
servidores para dar suporte a scripts desatualizados. O Joomla
<img src="https://docs.joomla.org/images/4/4d/Compat_icon_3_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 3.x" /> e superior deve estar usando o PHP7.x.
(Veja
<a href="https://downloads.joomla.org/br/technical-requirements-pt-br"
class="external text" target="_blank"
rel="noreferrer noopener">Requisitos do Joomla</a>)

### Usar arquivos php.ini locais

Em servidores compartilhados, você não pode editar o arquivo php.ini
principal, mas pode adicionar arquivos php.ini locais e personalizados.
Nesse caso, você precisará copiar os arquivos php.ini para cada
subdiretório que requeira configurações personalizadas.

**Há algumas coisas importantes a ter em mente.**

1.  Arquivos *php.ini* locais ***somente*** têm efeito se seu servidor
    estiver configurado para usá-los. Isso inclui um arquivo *php.ini*
    em seu diretório *http_root*. Você pode testar se esses arquivos
    afetam ou não seu site definindo uma diretiva óbvia no arquivo
    *php.ini* local para ver se isso afeta seu site.
2.  Arquivos *php.ini* locais afetam somente arquivos *.php* que estão
    localizados dentro do mesmo diretório (ou included() ou required()
    desses arquivos). Isso significa que normalmente existem apenas dois
    diretórios do Joomla! nos quais você iria querer colocar um arquivo
    *php.ini*. Eles são o seu *http_root*(seu nome de diretório real
    pode variar), que é onde o arquivo *index.php* do front-end do
    Joomla está localizado, e o diretório *administrator* do Joomla!,
    que é onde o arquivo *index.php* do backend do administrador está
    localizado. Outros diretórios que não possuem arquivos chamados via
    web não precisam de arquivos *php.ini* locais.
3.  Se você tem um arquivo *php.ini* em cada diretório, algum script
    provavelmente fez isso por você. Se você não pretendia que isso
    acontecesse, você provavelmente deveria eliminá-los, mas dado o \#2
    acima, você provavelmente só precisa entrar em pânico com os
    arquivos *php.ini* nos diretórios *http_root* e *administrator*.

### Usar o disable_functions do PHP

Use o *disable_functions* para desabilitar funções perigosas do PHP que
não são necessárias ao seu site. Aqui está uma configuração típica para
um site Joomla!:

         disable_functions = show_source, system, shell_exec, passthru, exec, phpinfo, popen, proc_open

### Considerar usar o open_basedir do PHP

Você *pode* considerar habilitar o *open_basedir*. Esta diretiva limita
os arquivos que podem ser abertos pelo PHP à árvore de diretórios
especificada. Esta diretiva não é afetada pelo modo de segurança estar
ligado ou desligado.

A restrição especificada com open_basedir é um prefixo, não um nome de
diretório. Isto significa que *open_basedir = /dir/incl* permite acesso
a */dir/include* e */dir/incls* se existirem. Para restringir o acesso
apenas ao diretório especificado, termine com uma barra. Para obter mais
informações, consulte <a
href="http://us3.php.net/manual/en/features.safe-mode.php#ini.safe-mode"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Diretivas de configuração de
segurança e modo de segurança do PHP</a>.

        open_basedir = /home/users/you/public_html

Além disso, se *open_basedir* estiver definido, pode ser necessário
definir a diretiva de configuração *upload_tmp_dir* do PHP para um
caminho que esteja dentro do escopo de *open_basedir* ou,
alternativamente, adicionar o caminho *upload_tmp_dir* para
*open_basedir* usando o separador de caminho apropriado para o sistema
do host.

        open_basedir = /home/users/you/public_html:/tmp

O PHP usará o diretório temporário do sistema quando *upload_tmp_dir*
não estiver definido ou quando estiver definido mas o diretório não
existir, portanto, pode ser necessário adicioná-lo a *open_basedir* como
acima para evitar erros de upload no Joomla .

### Ajustar o magic_quotes_gpc

**<span class="small">*Este recurso do PHP foi depreciado a partir do
PHP 5.3.0 (30-06-2009) e foi removido do PHP a partir do PHP
5.4.0.*</span>**

Ajuste a diretiva *magic_quotes_gpc* conforme necessário para seu site.

- O Joomla! 3.0 e acima **requer** o *magic_quotes_gpc* desativado e não
  será instalado se o *magic_quotes_gpc* estiver ativado.
- O Joomla! aconselha que o *magic_quotes_gpc* seja desativado ao usar o
  Joomla 2.5.xx.
- O Joomla! 1.5 ignora a configuração magic_quotes e funciona bem de
  qualquer maneira. O método mais seguro é desligar o magic_quotes_gpc e
  evitar todas as extensões mal escritas.
- A configuração recomendada para o Joomla! 1.0.x é ativado para
  proteger contra extensões de terceiros mal escritas.

Para mais informações, consulte  Citações mágicas e
segurança
ou <a href="http://php.net/magic_quotes" class="external text"
target="_blank" rel="nofollow noreferrer noopener">Manual do PHP,
Capítulo 31. Citações mágicas</a>.

    to turn off    magic_quotes_gpc = 0
    to turn on     magic_quotes_gpc = 1

### Não usar o safe_mode do PHP

**<span class="small">*Este recurso do PHP foi descontinuado a partir do
PHP 5.3.0 e removido a partir do PHP 5.4.0*</span>**

Confiar nesse recurso é altamente desencorajado. Evite o uso do
safe_mode do PHP. Esta foi uma tentativa de resolver problemas de
segurança compartilhada e fornece uma falsa sensação de segurança. O
modo de segurança também pode causar problemas de propriedade com
aplicativos e quaisquer arquivos criados pelos aplicativos. Consulte o
site oficial do PHP para mais informações.
<a href="http://php.net/manual/en/features.safe-mode.php"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Manual do PHP: Modo de segurança</a>

         safe_mode = 0

### Não usar register_globals do PHP

**<span class="small">*Este recurso do PHP foi descontinuado a partir do
PHP 5.3.0 e removido a partir do PHP 5.4.0*</span>**

O registro automático de variáveis globais foi provavelmente uma das
decisões mais estúpidas que os desenvolvedores do PHP tomaram. Esta
diretiva determina se as variáveis EGPCS (Environment, GET, POST,
Cookie, Server) devem ou não ser registradas como variáveis globais onde
elas se tornam imediatamente disponíveis para todos os scripts PHP, e
onde elas podem facilmente substituir sua própria variável se você não
tomar cuidado . Felizmente, os desenvolvedores PHP há muito tempo
perceberam o erro e desaprovaram esse "recurso".

Se o seu site estiver em um servidor compartilhado com um provedor de
hospedagem que insiste que o *register_globals* deve estar ativado, você
deve ficar muito preocupado. Embora muitas vezes você possa desativar o
register_globals para seu próprio site com um arquivo php.ini local,
isso adiciona pouca segurança, pois outros sites no mesmo servidor
permanecem vulneráveis a ataques que podem lançar ataques contra seu
site de dentro do servidor.

Para obter mais informações, consulte
<a href="http://php.net/manual/en/security.globals.php"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Manual do PHP: Usando registradores
globais</a>.

         register_globals = 0

### Não usar o allow_url_include do PHP

Não usar o *allow_url_include* do PHP. Esta opção do PHP permite que um
programador inclua um arquivo remoto usando uma URL em vez de um caminho
de arquivo local. Isso é inseguro. Se um aplicativo (ou extensão) puder
ser induzido a incluir conteúdo de uma URL fora de si mesmo, um invasor
poderá forçar o aplicativo (ou extensão) a iniciar a execução de código
de seu próprio site. Se um aplicativo ou extensão alegar exigir que esse
recurso funcione, você deve procurar alternativas, pois um requisito
para usar esse recurso indica falhas graves de projeto no aplicativo ou
extensão.

### Usar o allow_url_fopen

Esta opção habilita os wrappers fopen com reconhecimento de URL que
permitem acessar objetos de URL como arquivos. Os wrappers padrões são
fornecidos para o acesso de arquivos remotos usando o protocolo ftp ou
http, algumas extensões como a zlib podem registrar wrappers adicionais.
Nota: Isso só pode ser definido no php.ini por motivos de segurança.
**Ative e use allow_url_fopen para permitir que a atualização com um
clique do Joomla funcione corretamente.**

Para obter mais informações, consulte: <a
href="http://www.php.net/manual/pt_BR/filesystem.configuration.php#ini.allow-url-fopen"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Manual do PHP: allow_url_fopen e
allow_url_include</a>

       Proper setup will have this:
                    allow_url_fopen = 1
                  allow_url_include = 0

       PHP default: allow_url_fopen is enabled
       PHP default: allow_url_include is disabled

## Permissões de arquivo

Se uma instalação do Joomla estiver hospedada no Apache com mod_php,
todos os hosts virtuais nesse servidor serão executados no mesmo
contexto que seu código do Joomla. Se os arquivos são de propriedade de
algum outro usuário que não seja "nobody" ou "wwwrun", as permissões
mais seguras são aquelas que **impedem** alterações no código do Joomla,
a menos que sejam através de um canal autorizado (por exemplo, FTP:

- Diretório raiz de documento: 750 (por exemplo, public_html)
- Arquivos: 644
- Diretórios: 755 (711 se você for paranóico, mas não para diretórios
  que precisam ser listados) (proprietário: algum usuário)

Com essas permissões definidas, você precisará usar o FTP para atualizar
sua instalação do Joomla. Nem todos os módulos suportam isso. Remova os
módulos que não suportam atualizações de FTP.

Outros processos rodando sob o mod_php podem ler **seu**
configuration.php. Você pode frustrar hacks automatizados renomeando
este arquivo. Você não deve armazenar sua senha de FTP em seu arquivo de
configuração em tais hosts, pois sua conta *será* comprometida.

Se uma instalação do Joomla estiver hospedada no Apache com fast-cgi,
suphp ou cgi executado como um usuário diferente, você deve definir suas
permissões da seguinte forma:

- Diretório raiz de documento: 750 (por exemplo, public_html)
- Arquivos do PHP: 600 (400 se você for realmente paranóico)
- Arquivos HTML e de imagem: 644 (444 se você for realmente paranóico)
- Diretórios: 755 (711 se você for paranóico, mas não para diretórios
  que precisam ser listados)

**Se** o servidor em que você está requer permissões 777 para o Joomla
funcionar corretamente, então **solicite para ser colocado em outro
servidor** com php como cgi e suphp e software do lado do servidor
atualizado (apache, php etc) em seu host existente ou encontre outro
host de servidor, se necessário.

Verifique com seu provedor de hospedagem se eles protegeram
propositalmente o servidor em que seu site está; e que eles ou você
realizem atualizações de segurança regulares (semanais) para manter o
servidor atualizado. Verifique se você tem jail shell. Uma regra geral é
quanto menos você paga, menos eles se importam.

Mais informações sobre permissões de arquivo podem ser encontradas aqui:
## Configurar um processo de cópia de segurança e recuperação

### A regra mais importante

Você deve sempre poder retornar seu site a um estado de funcionamento
anterior por meio do uso regular de um processo de cópia de segurança e
recuperação forte e externo. Certifique-se de que seu processo de cópia
de segurança e recuperação esteja implementado e testado antes de entrar
em operação. Esta é a melhor (e muitas vezes a única) maneira de se
recuperar de catástrofes inevitáveis como:

1.  Site quebrado devido a uma atualização defeituosa.
2.  Falha de hardware, como discos rígidos inoperantes, falhas de
    energia, roubo de servidor, etc.
3.  Intervenção autoritária do governo. (Mais comum do que alguns
    pensam.)
4.  NePrecisar se mudar rapidamente para um novo servidor ou provedor de
    hospedagem.

As cópias de segurança não são recomendadas para restaurar um site
comprometido/hackeado, pois é possível que as cópias de segurança
contenham os arquivos alterados e hackeados. Usar as cópias de segurança
para restaurar um site invadido apenas restauraria o hack no site.
