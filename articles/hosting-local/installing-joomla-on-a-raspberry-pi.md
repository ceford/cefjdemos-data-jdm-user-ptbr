<!-- Filename: Installing_Joomla_on_a_Raspberry_Pi / Display title: Instalação do Raspberry Pi -->

## Prefácio

**Nota: Este documento ainda não está completo e totalmente testado.**

O <a href="https://www.raspberrypi.org/" rel="nofollow noreferrer noopener">Raspberry Pi</a> é um pequeno computador de placa única que foi originalmente desenvolvido para promover o ensino básico de ciência da computação em escolas e países em desenvolvimento. Devido à sua versatilidade, tornou-se muito popular e é usado como reprodutor de mídia, pequeno servidor autônomo, etc. Você pode usá-lo como servidor web e instalar o Joomla! nele. Esta página mostra como fazer o seu site Joomla! rodar no Raspberry Pi.

## Hardware

- **Raspberry Pi versão 3 Model B** - Existem vários modelos de Raspberry Pi. Você pode usar a maioria dos modelos que possuem uma porta Ethernet (os tipos Model B). No entanto, para melhor desempenho, usaremos a versão mais recente com mais memória RAM.
- **Cartão micro SD** - Para o sistema operacional + servidor web + Joomla. (A versão 3 do RPi modelo B usa micro SD; outras versões podem usar cartões SD normais)
- **Adaptador de 5 Volts (1 Amp)** - para alimentar o Raspberry Pi, você precisará converter a energia da rede (230V ou 110V) para 5 Volts. O Raspberry Pi precisa de cerca de 1 Amp, e talvez mais se você conectar dispositivos USB a ele.
- **Cabo Ethernet padrão** - para conectar o RPi à sua Rede Local / roteador / internet.

## Instalando o Sistema Operacional

O sistema operacional Raspbian é uma versão do Debian Linux especialmente compilada para o Raspberry Pi. Existem duas versões do <a href="https://www.raspberrypi.com/software/" rel="nofollow noreferrer noopener">Raspbian</a> disponíveis: **Raspbian Jessie com Pixel Lite** (versão com desktop PIXEL baseada no Debian Jessie) e **Raspbian Jessie Lite** (versão mínima baseada no Debian Jessie). Como usaremos o Raspberry Pi como um servidor web para o Joomla, não precisaremos da interface gráfica.

**Baixe** <a href="https://www.raspberrypi.org/downloads/raspbian/" rel="nofollow noreferrer noopener">Raspbian Jessie Lite</a> e descompacte o arquivo baixado, por exemplo, **2016-09-23-raspbian-jessie-lite.zip** (306 MB) para **2016-09-23-raspbian-jessie-lite.img** (1.4 GB).

Agora precisamos copiar o arquivo .img para o cartão (micro) SD. Você pode usar uma ferramenta com interface gráfica como o <a href="https://unetbootin.github.io/" rel="nofollow noreferrer noopener">UNetbootin</a> (para Windows, Mac OS X e Linux) ou fazer isso na linha de comando.

**Tenha cuidado** ao gravar a imagem de disco *.img* em outro disco. Se você especificar o disco de destino errado, irá sobrescrever esse disco com o *.img*, o que torna o disco inutilizável, resultando em perda de dados.

### Windows

Em um terminal (CMD), verifique qual dispositivo corresponde ao cartão SD e faça algo como:

```
    dd bs=1M if=c:\temp\2016-09-23-raspbian-jessie-lite.img of=[o dispositivo do seu cartão SD]
```

Veja também <a href="https://www.raspberrypi.org/documentation/installation/installing-images/windows.md" rel="nofollow noreferrer noopener">Instalando Imagens do Sistema Operacional usando Windows</a>

### Apple OSX

Verifique qual dispositivo está sendo usado pelo seu cartão SD. No nosso caso, é *disk1s1* e faremos no Terminal:

```
    sudo dd bs=1M if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/disk1s1
```

Veja também: <a href="https://www.raspberrypi.org/documentation/installation/installing-images/mac.md" rel="nofollow noreferrer noopener">Instalando Imagens do Sistema Operacional no MacOS</a>

### Linux

Conectamos um leitor de cartão SD com o cartão (micro) SD a um computador. Com *dmesg*, podemos encontrar o nome do dispositivo do cartão SD. No nosso caso, dmesg mostra algo como `[xxxxxx.xxxxxxx]  sdd: sdd1 sdd2`, significando que temos um cartão SD com 2 partições. Não escreva a imagem do Raspbian em uma partição, mas sim no disco inteiro **sdd**.

Usaremos o *dd* ("Disk Dump") para gravar um Arquivo de Entrada (*if*) em um Arquivo de Saída (*of*) usando um Tamanho de Bloco especificado (*bs*).

**Tenha cuidado**: *dd* gravará em um dispositivo sem nenhum aviso. Verifique duas vezes se você está escrevendo no dispositivo correto! Se você gravar no disco errado, sempre se lembrará do comando *dd* como "Destruidor de Disco".

```bash
    sudo dd if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/sdd bs=4M
```

Veja também <a href="https://www.raspberrypi.org/documentation/installation/installing-images/linux.md" rel="nofollow noreferrer noopener">Instalando Imagens do Sistema Operacional no Linux</a>

**AVISO para a versão Raspbian Stretch**: para ter um servidor SSH funcionando desde o boot, você precisa criar um arquivo vazio *ssh* na partição raiz.

## Conectando o Raspberry Pi à LAN

Quando instalamos o sistema operacional Raspbian no cartão SD, vamos:

- Inserir o cartão micro SD no slot de cartão SD no Raspberry Pi.
- Conectar um cabo Ethernet ao Raspberry Pi e à Rede Local (conectar ao nosso roteador).
- Conectar a fonte de alimentação de 5V ao Raspberry Pi.

Inicializar o Raspberry Pi leva cerca de 30 segundos. Precisamos encontrar o endereço IP para conectá-lo usando SSH. Podemos usar diferentes abordagens para isso:

- entrar na interface web do seu roteador e verificar os dispositivos conectados;
- usar um telefone celular conectado ao roteador wi-fi usando um aplicativo de escaneamento de rede chamado **Fing Overlook**;
- usar um comando como **nmap**. Supondo que nosso PC tenha o endereço IP **192.168.0**.25, podemos encontrar todos os outros dispositivos no mesmo intervalo de rede fazendo o seguinte:
```
    sudo nmap -sP 192.168.0/24
```
O que pode mostrar os seguintes detalhes:

    Starting Nmap 6.47 (http://nmap.org) at 2016-10-22 17:42 CEST
    Nmap scan report for 192.168.0.35
    Host is up (0.00042s latency).
    MAC Address: 42:42:42:42:42:42 (Raspberry Pi Foundation)

Para fazer login no nosso Raspberry Pi, usaremos o comando **ssh**.

```
    ssh pi@192.168.0.35
```

Na primeira vez que você se conectar, aparecerá algo assim:

    A autenticidade do host '192.168.0.35 (192.168.0.35)' não pode ser estabelecida.
    A impressão digital da chave ECDSA é 42:42:42:42:42:42:42:42:42:42:42:42:42:42:42:42.
    Tem certeza de que deseja continuar conectando (sim/não)?

Escolheremos **Sim**

    Aviso: Adicionado permanentemente 192.168.0.35 (ECDSA) à lista de hosts conhecidos.
    senha para pi@192.168.0.35: 

e usaremos a *senha padrão*: *raspberry*, que ao fazer login com sucesso, mostrará:

    Os programas incluídos no sistema Debian GNU/Linux são software livre;
    os termos exatos de distribuição para cada programa são descritos nos arquivos
    individuais em /usr/share/doc/*/copyright.

    Debian GNU/Linux vem SEM QUALQUER GARANTIA, na medida
    permitida pela lei aplicável.
    pi@raspberrypi:~ $

Podemos configurar o Raspberry Pi usando uma interface de texto via:

    sudo raspi-config

### Ferramenta de Configuração de Software Raspberry Pi (raspi-config)

Com esta ferramenta de configuração, alteraremos apenas as seguintes configurações.

#### 1 Expandir Sistema de Arquivos

Por padrão, o espaço em disco no cartão SD tem o mesmo tamanho que o arquivo .img de 1.4GB que você usou para criar o cartão SD para seu Raspberry Pi. Você pode usar esta opção para ganhar o restante do espaço em disco.

#### 2 Alterar Senha do Usuário

Por razões de segurança, é melhor **mudar a senha padrão** "raspberry" o mais rápido possível.

#### 3 Opções de Inicialização

Gostaríamos que o Raspberry Pi inicializasse no console de texto

##### B2 Console Autologin Console de texto, automaticamente logado como usuário 'pi'

#### 9 Opções Avançadas

##### A3 Divisão de Memória

Como usaremos o Raspberry Pi como um servidor sem cabeça, sem conectá-lo a um monitor, podemos diminuir a memória usada pela GPU de 64 para **16**

#### 5 Opções de Internacionalização

##### I2 Mudar Fuso Horário

Mudaremos o Fuso Horário para nosso próprio fuso (por exemplo, Europa/Amsterdã)

Depois de todas as mudanças, reiniciaremos o Raspberry Pi e faremos login novamente com nossa nova senha.

    ssh pi@192.168.0.35

Agora é hora de instalar o restante.

## Atualizar software

Antes de instalar qualquer outra coisa, vamos:

- **atualizar** a lista de versões do software de todos os repositórios externos
    ```shell
    sudo apt-get update
    ```

- **atualizar** todo o software instalado
    ```shell
    sudo apt-get upgrade
    ```

**Atualizar a lista de versões e atualizar todo o software é algo que
deve ser feito regularmente.**

## Servidor Web Nginx

Uma alternativa rápida e leve ao servidor web Apache é o cada vez mais popular servidor web **Nginx**.

### Instalação do Nginx

Vamos instalar o nginx e todas as dependências (leia-se: software que o nginx precisa para funcionar) com

    sudo apt-get install nginx

Receberemos uma mensagem como:

    Lendo listas de pacotes... Pronto
    Construindo árvore de dependências       
    Lendo informações de estado... Pronto
    Os seguintes pacotes extras serão instalados:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx-common nginx-full
    Pacotes sugeridos:
     libgd-tools fcgiwrap nginx-doc ssl-cert
    Os NOVOS pacotes a seguir serão instalados:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx nginx-common nginx-full
    0 atualizados, 12 novos instalados, 0 a serem removidos e 0 não atualizados.
    É necessário baixar 3,550 kB de arquivos.
    Depois dessa operação, 8,666 kB adicionais de espaço em disco serão utilizados.
    Você deseja continuar? [S/n] s

Escolhendo "s", o nginx e todos os pacotes necessários serão instalados.

Você pode verificar a instalação com um navegador. Vá para o endereço IP do seu Raspberry Pi, no nosso caso
<a href="http://192.168.0.35/"
rel="nofollow noreferrer noopener">http://192.168.0.35/</a> Devemos ver uma mensagem como:

    Bem-vindo ao nginx no Debian!
    Se você vê esta página, o servidor web nginx está instalado com sucesso e funcionando no Debian. É necessário mais configuração.
    Para documentação e suporte online, consulte nginx.org
    Utilize a ferramenta reportbug para relatar bugs no pacote nginx com o Debian.
    No entanto, verifique relatórios de bugs existentes antes de relatar um novo bug.
    Obrigado por usar debian e nginx.

#### Iniciando e parando o Nginx

Após a instalação, o Nginx será iniciado automaticamente. Você pode:

- Parar o Nginx: sudo service nginx stop
- Iniciar o Nginx: sudo service nginx start
- Reiniciar o Nginx: sudo service nginx restart

### Configurar Nginx

#### Configuração Global do Nginx

Na configuração global do Nginx, podemos configurar cache padrão etc. O Raspberry Pi 3 usa um processador **quad-core** ARM Cortex-A53 de 1.2 GHz e 64 bits. Se você tiver uma versão anterior com menos núcleos de CPU, então você deve usar

    sudo nano /etc/nginx/nginx.conf

para mudar "worker_processes" para se ajustar à quantidade de CPUs do seu dispositivo. Por padrão, está configurado como

    worker_processes 4;

então para o Raspberry Pi 3, você não precisa mudar.

Após alterar a configuração do Nginx ou de domínios virtuais, você tem que fazer um

    sudo nginx reload

para que as alterações tenham efeito.

#### Domínios Virtuais

É possível executar vários sites Joomla no mesmo servidor usando domínios virtuais.

Coloque cada site em uma pasta separada no diretório padrão /var/www/ por exemplo:

- /var/www/example.com/
- /var/www/voorbeeld.nl/
    sudo mkdir /var/www/example.com
    sudo mkdir /var/www/voorbeeld.nl

Para cada site, vamos criar um domínio virtual que é basicamente um arquivo de texto com informações específicas do domínio:

- /etc/nginx/sites-available/example.com
    server {
    listen 80;
    server_name example.com www.example.com;
    root /var/www/example.com;

    access_log /var/log/nginx/example.com.access_log;
    error_log /var/log/nginx/example.com.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

- /etc/nginx/sites-available/voorbeeld.nl
    server {
    listen 80;
    server_name voorbeeld.nl www.voorbeeld.nl;
    root /var/www/voorbeeld.nl;

    access_log /var/log/nginx/voorbeeld.nl.access_log;
    error_log /var/log/nginx/voorbeeld.nl.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

Precisamos habilitar cada site vinculando de /etc/nginx/sites-enabled/ ao domínio virtual em "sites-available". Criamos um link simbólico para cada domínio virtual:

    sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
    sudo ln -s /etc/nginx/sites-available/voorbeeld.nl /etc/nginx/sites-enabled/voorbeeld.nl

Para que essa configuração de domínio virtual tenha efeito, fazemos

    sudo nginx reload

e quando tudo estiver configurado corretamente, ele responderá:

    Recarregando configuração nginx: nginx.

## Banco de Dados

Podemos instalar MariaDB ou MySQL; o Joomla funcionará com ambos. Vamos instalar o MariaDB com:

```bash
sudo apt-get install mariadb-server
```

Durante a instalação, você precisará adicionar uma senha para o usuário **root**. Vamos criar uma **senha de banco de dados**, por exemplo, **correcthorsebatterystaple**.

Finalmente, vamos melhorar a segurança da nossa instalação do MariaDB removendo contas root que são acessíveis de fora do host local, contas de usuários anônimos e o banco de dados de teste. Podemos fazer isso com:

```bash
mysql_secure_installation
```

## PHP

Para o PHP, vamos instalar o **php-fpm** (FastCGI Process Manager), que roda como um daemon e recebe requisições Fast/CGI. Além disso, vamos instalar o **php5-mysql**, que é um módulo para conexões com bancos de dados MySQL diretamente a partir de scripts PHP.

A versão mais recente, php7, deve ser instalada com

```bash
sudo apt-get install php-fpm php-mysql
```

Agora, precisamos informar ao Nginx que ele deve usar php-fpm para arquivos .php. Adicionamos algumas linhas aos nossos domínios virtuais:

```bash
sudo nano /etc/nginx/sites-available/example.com
```

Adicione:

```nginx
location ~ \.php$ {
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    fastcgi_index index.php;
    include fastcgi_params;
}
```

Teste criando o seguinte arquivo PHP

```bash
sudo nano /var/www/example.com/test.php
```

Use um navegador para testar se você vê a página de configuração do PHP em
<a href="http://192.168.0.35/example.com/test.php" rel="nofollow noreferrer noopener">http://192.168.0.35/example.com/test.php</a>

## Joomla!

- a fazer
```
    sudo wget https://github.com/joomla/joomla-cms/releases/download/3.6.3/Joomla_3.6.3-Stable-Full_Package.zip
    sudo unzip -x Joomla_3.6.3-Stable-Full_Package.zip
```

## Conectando Raspberry Pi à Internet

Queremos que as pessoas na internet possam visitar nosso site Joomla no
nosso Raspberry Pi. Para isso, precisamos **configurar nosso roteador
de Internet** para redirecionar todo o **tráfego de entrada** na porta 80 **para
nosso Raspberry Pi**.

Use seu navegador para se conectar à interface web do seu roteador. Um
roteador geralmente está localizado no primeiro número de sua faixa de IP, no nosso
caso em 192.168.0.1. No nosso roteador, configuramos o **Encaminhamento de Porta**:

- Endereço IP Externo: 0.0.0.0
- Porta Inicial Externa: 80
- Porta Final Externa: 80
- Endereço IP Interno: 192.168.0.35 (= nosso Raspberry Pi)
- Porta Inicial Interna: 80
- Porta Final Interna: 80
- Protocolo: TCP

Certifique-se de que está habilitado.

Se tudo estiver funcionando corretamente, você deverá ver seu próprio site Joomla
no Raspberry Pi ao visitar seu endereço IP externo (Encontre
seu endereço IP externo com uma ferramenta como o
<a href="http://www.whatsmyip.org/"
rel="nofollow noreferrer noopener">whatsmyip.org</a>).

### Usando um nome de domínio

Vamos supor que nosso endereço IP externo é 42.42.42.42. Vamos também
supor que registramos um nome de domínio chamado exemplo.com. Queremos
servir nosso site Joomla no nosso Raspberry Pi para visitantes que
visitem exemplo.com. Se o registrador do seu nome de domínio nos der a
possibilidade de configurar o servidor do **Sistema de Nomes de Domínio (DNS)**,
então precisaremos criar um **registro MX** no DNS que aponte nosso
**nome de domínio para** nosso **endereço IP** 42.42.42.42. Note que pode levar
até 24 horas para que todos os provedores de internet redirecionem o tráfego de
seus clientes para o registro MX configurado.

### Endereço IP estático

A maioria dos roteadores continuará atribuindo o mesmo endereço IP interno ao seu
Raspberry Pi. Às vezes, é melhor configurar seu Raspberry Pi para
usar um endereço IP estático:

```bash
sudo nano /etc/network/interfaces
```

modifique

```bash
iface eth0 inet static
```

para

```bash
iface eth0 inet static
address 192.168.0.35
netmask 255.255.255.0
gateway 192.168.0.1
```

O gateway é o endereço IP do seu roteador. Você também pode encontrá-lo usando

```bash
route
```

# Links externos

- <a href="https://raspberrypi.org"
  rel="nofollow noreferrer noopener">Raspberry Pi Foundation</a> (RPF) -
  site oficial e fóruns
- <a href="http://elinux.org/RaspberryPiBoard"
rel="nofollow noreferrer noopener">Raspberry Pi Wiki</a>,
  suportado pela RPF
- Vídeo da apresentação
  <a href="https://youtu.be/u2MFQCoexD0"
  rel="nofollow noreferrer noopener">Joomla no Raspberry
  Pi (com Nginx)</a> no Joomladay Alemanha 2013 em Nuremberg, Alemanha

*Traduzido por openai.com*

