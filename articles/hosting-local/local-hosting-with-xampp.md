<!-- Filename: / Display title: Hospedagem Local com XAMPP  -->

## Introdução

O XAMPP é um pacote fácil de instalar que inclui o servidor web Apache, PHP, XDEBUG e o banco de dados MySQL. Isso permite que você crie o ambiente necessário para executar o Joomla! na sua máquina local. A versão mais recente do XAMPP está disponível no site [Apache Friends](https://www.apachefriends.org/index.html). Há downloads disponíveis para Linux, Windows e Mac OS X. Baixe o pacote para a sua plataforma.

*Nota Importante sobre XAMPP e Skype:* Tanto o Apache quanto o Skype utilizam a porta 80 como uma alternativa para conexões de entrada. Se você usa Skype, vá ao painel Ferramentas-Opções-Avançado-Conexão e desmarque a opção *Usar 80 e 443 como alternativas para conexões de entrada*. Se o Apache iniciar como um serviço, ele ocupará a porta 80 antes do Skype iniciar, e você não terá problemas. Mas, para estar seguro, desative a opção no Skype.

## Instalação

A instalação em qualquer plataforma é muito simples - utilize o Instalador. Não há um manual verdadeiro ou guia para o XAMPP. A documentação está na forma de FAQs, vinculadas à página de Downloads.

### Instalação no Windows

Para Windows, é recomendado instalar o XAMPP em "c:\xampp" (e não em "c:\arquivos de programas"). Se você fizer isso, seu Joomla! (e qualquer outra pasta de sites locais) ficará na pasta "c:\xampp\htdocs". (Por convenção, todo o conteúdo da web vai para a pasta "htdocs".)

Se você tiver múltiplos servidores http (como o IIS), você pode alterar a porta de escuta do xampp. No arquivo \apache\conf\httpd.conf, modifique a linha Listen 80 para Listen \[numerodaporta\] (ex: "Listen 8080").

<div class="alert alert-info">
<h4>Tutorial da Revista da Comunidade Joomla<h4>
<p>Você pode encontrar um tutorial detalhado sobre a instalação do XAMPP no Windows, junto com o Joomla 4 Beta, o Joomla Patch Tester e o Git neste <a href="https://magazine.joomla.org/all-issues/june-2020/github-installing-git"
rel="noreferrer noopener">artigo da Revista da Comunidade Joomla</a>.</p></div>

Para instalar o XDebug: [XAMPP - Configuração do XDebug para PHP 8](https://odan.github.io/2020/12/03/xampp-xdebug-setup-php8.html)

### Instalação no Linux

#### Instalar XAMPP

A página de Download baixa um instalador xampp-linux-x64-8.2.12-0-installer.run onde 8.2.12 é a versão mais recente. Execute o arquivo do instalador para instalar o Apache2, MySQL e PHP.

Após a instalação, use os seguintes comandos para iniciar e parar os serviços:
```sh
    sudo /opt/lampp/lampp start
    sudo /opt/lampp/lampp stop
```

#### Teste seu servidor localhost XAMPP

Abra seu navegador e aponte para

    http://localhost

O index.php redirecionará para

    http://localhost/xampp

Lá, você encontrará instruções sobre como alterar nomes de usuários/senhas padrão. Em um PC que não serve arquivos para a Internet ou LAN, alterar os padrões é uma decisão pessoal.

#### Obter Joomla

* Baixe o mais recente zip de instalação do Joomla
* Extraia para seu disco rígido
* Conecte-se ao localhost com um cliente FTP Padrão
* Crie uma pasta para seu Joomla no servidor localhost
* FTP os arquivos de instalação descompactados do Joomla para a pasta recém-criada do Joomla.

##### Importante:

- A instalação do xammp define a Propriedade correta dos arquivos e permissões.
- Usar o **comando CHOWN** irá **causar problemas de Propriedade com xampp**.
- **Usar o nautilus** para manipular pastas/arquivos no localhost irá **causar problemas de Propriedade com xampp**.

#### Informações do banco de dados

- Host: localhost
- Nome padrão do banco de dados: test
- Usuário padrão do banco de dados: root
- Senha padrão: Não há **nenhuma** senha padrão.
- Senha do administrador: sua escolha.

É recomendada a instalação de Dados de Amostra para o usuário iniciante.

Após a instalação, exclua o diretório de instalação e aponte seu Navegador para: `http://localhost/suanovapastadojoomla` ou `http://localhost/suanovapastadojoomla/administrator`.

#### Criando um link no menu do Ubuntu

##### Para criar uma interface gráfica para xammp conectada ao seu menu do Ubuntu

Abra o Terminal e digite

    sudo nano /usr/share/applications/xampp-control-panel.desktop

Em seguida, copie o seguinte para o editor nano e salve.

    [Desktop Entry]
    Encoding=UTF-8
    Name=XAMPP Control Panel
    Comment=Start and Stop XAMPP
    Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
    Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Network;
    StartupNotify=true

Se o painel de controle falhar ao iniciar, tente executar o comando Exec diretamente no terminal:

    gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"

Se você receber o erro:

    Error importing pygtk2 and pygtk2-libglade

Instale as bibliotecas ausentes:

    sudo apt-get install python-glade2

#### Depurador PHP XDebug

O pacote XAMPP para Linux não inclui o depurador PHP XDebug. Para instalar o XDebug no Debian ou Ubuntu:

- Instale o pacote *build-essential*:

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install autoconf

- Baixe o [pacote de desenvolvimento](http://www.apachefriends.org/en/xampp-linux.html) para sua versão do XAMPP e extraia-o sobre sua instalação existente:

    sudo tar xvfz xampp-linux-devel-1.7.7.tar.gz -C /opt

- Compile o XDebug:

    wget http://xdebug.org/files/xdebug-2.1.3.tgz
    tar xzf xdebug-2.1.3.tgz
    cd xdebug-2.1.3/
    /opt/lampp/bin/phpize

Após isso, você terá a seguinte saída no seu console…

    Configuring for:
    PHP Api Version:         20090626
    Zend Module Api No:      20090626
    Zend Extension Api No:   20090626

    ./configure --with-php-config=/opt/lampp/bin/php-config
    make
    sudo make install

Em seguida, a saída será esta.. por favor, monitore o diretório especificado.

    Installing shared extensions:     /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Crie uma pasta em sua pasta temporária que conterá o arquivo de dados gerado pelo XDebug:

    sudo mkdir /opt/lampp/tmp/xdebug
    sudo chmod a+rwx -R /opt/lampp/tmp/xdebug

Instalações alternativas:

Instale usando a biblioteca da comunidade de extensões do PHP (PECL) incluída com xampp:

    sudo /opt/lampp/bin/pecl install xdebug

No Ubuntu/Debian você pode instalar usando:

    apt-get install php5-xdebug

(aviso: isso também instalará o Apache e o PHP dos repositórios apt).

##### Aviso para usuários de 64 bits

Ao compilar XDebug ou instalar via apt-get, você receberá um erro ao (re)iniciar xampp:

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so: wrong ELF class: ELFCLASS64

Isso ocorre porque o xampp roda em 32 bits mas o XDebug é 64 bits. Para superar esse problema, faça xdebug.so em uma máquina de 32 bits ou baixe de:

    http://code.activestate.com/komodo/remotedebugging/

Baixe o arquivo: "PHP Remote Debugging Client" para "Linux (x86)" Extraia o conteúdo do arquivo em seu computador; este arquivo comprimido contém várias pastas com números de versão, ex: 4.4, 5.0, 5.1 ... 5.3 e assim por diante; entre na pasta com o número de versão mais alta ou aquela que funciona para você, então copie manualmente o arquivo "xdebug.so" para o seguinte local, substitua se necessário

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Lembre-se de que este local pode ser diferente em seu computador

### Instalação no Mac OS X

O Mac OS X já inclui um servidor Apache nativamente, mas a maioria dos desenvolvedores prefere usar as ferramentas integradas e a configurabilidade oferecida pelo XAMPP.

Como na maioria dos programas no Mac, a instalação é rápida. Visite o site do [Apache Friends](https://www.apachefriends.org/) e faça o download do instalador (xampp-osx-8.2.4-0-installer.dmg). Clique duas vezes no instalador baixado para iniciar o processo de instalação.

Para iniciar o servidor, abra "XAMPP Control.app" e pressione o botão iniciar ao lado do Apache.

#### Um Pouco de Solução de Problemas

Muitos usuários de Mac têm alguma dificuldade nesta etapa ao tentar configurar outra instância do Apache em sua máquina. Se você não conseguir iniciar o Apache do XAMPP, você tem duas opções:
**Você pode alterar a porta de escuta do XAMPP.** Em \Applications\XAMPP\xamppfiles\etc\httpd.conf, modifique a linha que diz, "Listen 80" para Listen \[numeroPorta\]. Exemplo:

    Listen 8080

**Você pode alterar a porta de escuta do servidor Apache pré-instalado.** No finder, vá para "/etc" (CMD+SHIFT+G); a partir daqui você poderá navegar pelos arquivos normalmente ocultos do Apache. Encontre a pasta rotulada como Apache2 e edite o arquivo "http.conf". Modifique a linha que diz, "Listen 80" para Listen \[numeroPorta\]. Exemplo:

    Listen 8080

*Nota: Se você escolher alterar a porta do servidor Apache pré-instalado, pode ser necessário reiniciar o computador para que as alterações entrem em vigor. Você também precisará se autenticar como administrador para alterar esses arquivos.*

### Testar a Instalação do XAMPP

Após instalar o XAMPP e ter iniciado o serviço Apache com a ferramenta de Painel de Controle do XAMPP, você pode testá-lo abrindo seu navegador e navegando para `http://localhost`. Você deve ver a tela de boas-vindas do XAMPP semelhante à abaixo.

![A página inicial do xampp](../../../en/images/hosting/local-hosting-xampp.png)

Selecione o link chamado `phpinfo()` no menu superior. Isso exibirá uma longa tela de informações sobre a configuração do PHP, conforme mostrado abaixo.

![A página de informações da versão do php do xampp](../../../en/images/hosting/local-hosting-xampp-php.png)

Neste ponto, o XAMPP está instalado com sucesso. Observe o *Arquivo de Configuração Carregado*. Estaremos editando este arquivo na próxima seção para configurar o XDebug.

*Traduzido por openai.com*

