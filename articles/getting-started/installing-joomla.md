<!-- Filename: J4.x:Installing_Joomla / Display title: Instalando o Joomla -->

## Introduction

Instalar o Joomla! pela primeira vez é muito fácil. O instalador web
integrado do Joomla facilita muito a configuração do seu novo site.

### Hosting Setup

If you have not yet set up a hosting environment you need to do it now,
either on a hosting service or your local computer. Read the  Hosting
Setup
tutorial for details.

Also, there are some PHP settings that need to be sufficient for Joomla
to install. The settings are usually in a *php.ini* or *user.ini*
configuration file on the server. If you are on shared hosting, talk to
your hosting service about how to change these settings if it is
possible to do so. If working on a localhost, for example with
XAMPP, or a
VPS or dedicated host, you should not be restricted by these settings
and can set them yourself.

The minimum values for the *php.ini* file are shown below:

- memory_limit - **Mínimo:** 64M **Recomendado:** 128M ou melhor
- upload_max_filesize - **Mínimo:** 30M
- post_max_size - **Mínimo:** 30M
- max_execution_time: **Recomendado:** 30

It is possible to work with lower values of upload_max_filesize and
post_max_size but larger extensions will fail to upload and cause
unpredictable problems.

### Database Setup

If you have not yet set up a database do it now. It is covered for a
hosting service in the  Hosting
Setup
tutorial. There is also a  Creating a Database for
Joomla!
tutorial that covers localhost and phpMyAdmin methods.

1.  Se você precisa criar um banco de dados, por favor leia "**[Criando
    um banco de dados para o
    Joomla](https://docs.joomla.org/Creating_a_Database_for_Joomla!/pt-br "Creating a Database for Joomla!/pt-br")**"
    primeiro ou pule para o passo \#2.
2.  Você terá que anotar as informações básicas do banco de dados
    necessárias quando a instalação real do Joomla for iniciada.
    - Localização do banco de dados, localhost? Ou o servidor de um host
      específico, como *`servidordbd1.seudominio.com`*?
    - O nome do banco de dados
    - O nome do usuário do banco de dados
    - A senha do usuário do banco de dados

## Prepare-se para instalar

Você precisará concluir duas tarefas antes de instalar o Joomla em seu
servidor. Primeiro, você precisará baixar os arquivos do pacote Joomla.
Em seguida, você precisará ter um banco de dados para o Joomla usar.

### Baixando e carregando arquivos do pacote Joomla!

Baixe a atual versão noturna do

1.  Mova o pacote de instalação do Joomla baixado para o servidor. Use
    um <a href="https://en.wikipedia.org/wiki/FTP_Client" class="extiw"
    title="wikipedia:FTP Client">cliente FTP</a> para transferir os
    arquivos Joomla 4.x para o seu servidor. Existem vários disponíveis
    para uso, aqui está uma <a
    href="https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software"
    class="extiw" title="wp:Comparison of FTP client software">lista
    detalhada de clientes FTP</a>. Certifique-se de estar usando a
    versão oficial de um cliente FTP.

Dica - Isso pode ser feito mais facilmente simplesmente movendo o pacote
baixado para o seu servidor e descompactando-o. Alternativamente, você
pode descompactar os arquivos em seu computador local e, em seguida,
mover os arquivos de instalação do Joomla para o seu servidor. De
qualquer forma, a instalação do Joomla precisa estar descompactada na
raiz do seu site.

Pasta "raiz" do seu servidor

Normalmente você carrega seus arquivos web para a pasta raiz. Ela
geralmente é chamada de "public_html", mas outras variações incluem
"htdocs" e isso depende de como seu host configurou o servidor. Para os
propósitos do Joomla, você pode carregar os arquivos diretamente em
"public_html" ou em uma subpasta que você criou dentro dela.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Aviso!

The zip package files can be extracted directly on the host using
various command line tools (e.g. unzip), which needs to be installed on
the server. If your hosting service uses the admin tool cPanel, the
Extract button can be pressed in the File Manager. Apart from that, the
free third-party tool
<a href="https://www.akeeba.com/products/akeeba-kickstart.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Akeeba Kickstart</a> may also be used
for this purpose. The unzipped files and directories will be placed in
the current folder. Extraction on your local computer depends on your
OS. Try a right-click and see if there is an extract menu. In this case
your OS may put the files in a folder with the same name as the zip
file. After extraction you may delete the zip file and rename the
extraction folder to something short and suitable for use in a url.

## Iniciar instalação

### Configuração principal

Com os requisitos acima atendidos, um banco de dados criado e os
arquivos Joomla necessários, você está pronto para instalar o Joomla.
Inicie o instalador web do Joomla abrindo seu navegador favorito e
navegando até o nome de domínio do site. Na instalação da hospedagem
você usará

*`https://www.yoursitename.com`*. Se você estiver instalando o Joomla
localmente, você usará *`http://localhost/`* e você deve ver a tela de
instalação.

<img
src="https://docs.joomla.org/images/0/06/J4x_Installation_screen_page_1.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="397" width="500" height="397"
alt="J4x Installation screen page 1.png" />

O Joomla tentará identificar o campo **Selecionar linguagem**
automaticamente a partir do idioma do seu navegador. Você pode alterar
isso, se necessário.

Preencha as seguintes informações.

- **Nome do site**: O nome do seu site — pode ser alterado a qualquer
  momento posteriormente na página  Configuração global do
  site.

Quando tudo na primeira página estiver concluído, clique no botão
**Configurar dados de início de sessão** para prosseguir:

## Dados de início de sessão

Agora você deve ver a tela de dados de início de sessão.

<img
src="https://docs.joomla.org/images/6/66/J4x_Installation_screen_page_2.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="481" width="500" height="481"
alt="J4x Installation screen page 2.png" />

Preencha as seguintes informações.

- **Nome real**: O nome do Superusuário. É assim que o Joomla irá
  cumprimentá-lo quando você iniciar a sessão.
- **Nome de usuário da conta de superusuário**: O nome de usuário do
  **Superusuário**. Evite usar admin (por ser uma boa  Meu
  perfil
  na interface da *administração* para alterá-lo mais tarde.
- **Senha do administrador**: Lembre-se que o superusuário tem o
  controle máximo do site (frontal e bastidores), então tente usar uma
  senha difícil. Use  Meu
  perfil
  na interface da *administração* para alterá-la mais tarde.
- **Endereço de e-mail do superusuário**: O endereço de e-mail do
  superusuário. Insira um e-mail válido caso esqueça sua senha. Este é o
  endereço de e-mail onde você receberá um link para alterar a senha de
  administrador.

Quando tudo na segunda página estiver concluído, clique no botão
**Configurar conexão de banco de dados** para prosseguir:

## Configuração do banco de dados

### Definições de configuração

Você precisará inserir as informações sobre o banco de dados que você
usará para o Joomla! agora. Você também pode ler ou revisar [Criando um
banco de dados para o
Joomla!](https://docs.joomla.org/Creating_a_Database_for_Joomla! "Special:MyLanguage/Creating a Database for Joomla!").

<img
src="https://docs.joomla.org/images/4/4f/J40_Installation_screen_page_3.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="637" width="500" height="637"
alt="J40 Installation screen page 3.png" />

Para simplificar, estas instruções são uma referência à instalação com
um banco de dados
<a href="https://en.wikipedia.org/wiki/MySQLi" class="extiw"
title="wikipedia:MySQLi">MySQLi</a>. As instruções na página de
instalação são autoexplicativas, mas aqui estão elas novamente:

- **Tipo de banco de dados**: O MySQLi é o banco de dados comum usado
- **Nome do host**: Onde seu banco de dados está localizado. O comum é
  *`localhost`*, mas alguns hosts usam um servidor de banco de dados
  específico, como

*dbserver1.yourhost.com*.

- **Nome de usuário**: O nome de usuário usado para se conectar ao banco
  de dados.
- **Senha**: A senha do usuário do banco de dados.
- **Nome do banco de dados**: O nome do banco de dados.
- **Prefixo da tabela**: Isso é gerado automaticamente e pode ser uma
  etapa de segurança útil, mas você pode alterá-lo. Por exemplo, `jos3_`
  pode ser usado. Só não esqueça de colocar o caractere sublinhado

(`_`) no final do prefixo.

- **Criptografia de conexão**: especifica como a conexão com o banco de
  dados deve ser criptografada. Se você não sabe - então é melhor manter
  o padrão. No entanto, isso permite que as empresas que usam
  autenticação de uma ou duas vias para a conexão de banco de dados a
  forneçam.

Todas essas opções e mais podem ser editadas na página [Configuração
global do
site](https://docs.joomla.org/Help40:Site_Global_Configuration#Server "Special:MyLanguage/Help40:Site Global Configuration"),
em Opções do servidor após a conclusão da instalação. Observe que você
interromperá sua instalação se alterar essas configurações após a
instalação, a menos que tenha uma cópia completa do banco de dados atual
sendo usado pela instalação do Joomla. Os usos comuns seriam atualizar o
nome de usuário e a senha do banco de dados ou concluir uma mudança de
uma instalação existente para um novo host com parâmetros diferentes.

Depois de clicar no botão **Instalar Joomla**, você deverá ver o
logotipo do Joomla girando. Quando a instalação for concluída, você
deverá ver a página de sucesso!

## Finalizando

### Sucesso e finalização da instalação

Parabéns! O Joomla! 4 já está instalado. Se você quiser começar a usar o
Joomla do jeito certo sem  instalar idiomas
extras
há um último passo para completar a instalação. Você deve excluir a
**Pasta de instalação**. Clique em **Remover pasta de instalação** e uma
mensagem de sucesso aparecerá. Agora você pode navegar para o início de
sessão do **Painel do administrador** clicando em **Concluir e abrir a
administração** ou vá direto para o seu site clicando em **Concluir e
abrir o site**.

<img
src="https://docs.joomla.org/images/e/e0/J40_Installation_screen_page_4.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="318" width="500" height="318"
alt="J40 Installation screen page 4.png" />

If you want to start using Joomla right away without  installing extra
languages
you can select *Open Administrator* to go to the *Administrator
Dashboard* or select *Open Site* to go to the Site Home page.

Você pode ver uma seção com as configurações recomendadas do PHP.

- **Configurações recomendadas**: Estas configurações são recomendadas
  em sua configuração PHP, mas não impedirão que o Joomla! seja
  instalado. Você pode consultar as instruções acima sobre como elas
  podem ser alteradas se houver necessidade de fazê-lo.

### Instalando linguagens extras

Como parte do processo de instalação do Joomla, você tem a oportunidade
de instalar linguagens adicionais antes de concluir a instalação
excluindo a **Pasta de instalação**, clique em:

Para fazer isso, clique no botão Instalar linguagens adicionais

Isso o levará a uma página de instalação extra, permitindo que você
selecione as linguagens necessárias.

#### Instalar linguagens

Uma lista de pacotes de linguagens é exibida.

<img
src="https://docs.joomla.org/images/c/ce/J40_Installation_screen_page_5.png"
decoding="async" data-file-width="500" data-file-height="755"
width="500" height="755" alt="J40 Installation screen page 5.png" />

Selecione até 3 linguagens que você deseja instalar (selecionar mais de
3, de uma vez, pode causar problemas de tempo limite - você pode
instalar mais posteriormente).

Lembre-se do seguinte:

- Os pacotes de linguagens incluídos em distribuições personalizadas não
  serão listados neste estágio, pois já estão instalados.
- Uma versão dos pacotes propostos corresponderá à versão principal do
  Joomla (4.0.x, 4.1.x, etc.). A versão menor do pacote pode não
  corresponder, por exemplo você está instalando a versão 4.0.3 e um
  pacote de linguagem 4.0.2 é mostrado.
- Os pacotes de linguagens inigualados no exemplo acima podem ter
  strings não traduzidas.
- Os pacotes de linguagens inigualados serão oferecidos como uma
  atualização quando os pacotes forem atualizados pelas equipes de
  tradução registradas. A atualização disponível será mostrada no painel
  de controle, bem como no **Gerenciador de
  extensões **→** Atualização**. Este comportamento é semelhante ao
  **Gerenciador de extensões **→** Instalar linguagens**.

Clique em **Avançar** e uma barra de progresso será exibida enquanto
o(s) pacote(s) de linguagem(ns) estiver(em) sendo instalado(s).

#### Escolher a linguagem padrão

Quando a instalação das linguagens
estiver concluída, você será presenteado com um **Parabéns! O seu site
Joomla está pronto.** muito semelhante ao da imagem. A diferença será
uma lista das linguagens instaladas, permitindo que você selecione a
linguagem padrão para o site e para a interface do administrador.

<img
src="https://docs.joomla.org/images/d/d2/J40_Installation_screen_page_4_default_langs.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="650" width="500" height="650" alt="500" />

- Selecione a linguagem padrão que você deseja usar.
- Depois de selecionar a linguagem padrão, clique no botão **Definir
  idioma padrão** para confirmar.
- Uma mensagem do sistema será exibida confirmando que o Joomla definiu
  a linguagem padrão do administrador e do site. Essa mensagem pode ser
  fechada.

#### Finalizar

Agora você deve excluir a **Pasta de instalação**. Clique em **Remover a
pasta de instalação**. Você receberá uma mensagem de confirmação e agora
pode navegar para o início de sessão do **Painel do administrator**
clicando em **Concluir e abrir a administração** ou ir direto para o seu
site clicando em **Concluir e abrir o site**.

## Related Information

-  Hosting
  Setup
-  Hosting and Server
  Setup
-  Creating A VPS Testing
  Server
-  Setting up your local
  environment
-  Joomla CLI
  Installation
