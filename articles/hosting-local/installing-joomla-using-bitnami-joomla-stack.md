<!-- Filename: Installing_Joomla!_using_BitNami_Joomla!_stack / Display title: Instalação do Bitnami -->

## Prefácio

**NOTA:** O BitNami Joomla! stack não existe mais como um instalador autônomo. Em vez disso, ele é disponibilizado como: 1) Uma instância baseada em nuvem, 2) Em um contêiner, seja Kubernetes ou Docker, ou 3) Uma máquina virtual. A máquina virtual será executada no seu sistema operacional em um hipervisor como Virtual Box ou VMware Player. Ele ainda vem com todas as dependências necessárias, assim como no instalador autônomo.

A Opção 1 abaixo não se aplica mais. Além disso, na Opção 2, o BitNami Lamp Stack mais abaixo, é entregue na nuvem ou em uma máquina virtual. Em qualquer caso, o Bitnami facilita ter uma instalação local de alto desempenho do Joomla! de maneira fácil e completa.

Você pode baixar a versão mais recente do pacote Bitnami para Joomla! para Windows, Linux e Mac em <a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">http://bitnami.org/stack/joomla</a>.

**Revisão Necessária!**

O BitNami Joomla! Stack é um instalador completo que facilita a instalação do Joomla no seu computador. É gratuito, fácil de usar e autossuficiente. Isso significa que ele reúne e configura automaticamente todas as partes de software (dependências) necessárias para executar o Joomla, tanto para fins de desenvolvimento quanto de produção, incluindo o Apache HTTP Server, MySQL e PHP.

## Opção 1: Stack do Joomla! (Recomendado)

Este método assume que você já possui um ambiente 
(**W**indows/**L**inux/**M**ac)...**AMP** (Servidor HTTP Apache, MySQL e PHP) instalado.

### Instalando o Stack do Joomla!

Independentemente do sistema operacional que você está utilizando (Windows / Linux / Mac), o processo de instalação é o mesmo.

Baixe a versão mais recente do Stack do Joomla! no
<a href="http://bitnami.org/stack/joomla"
rel="nofollow noreferrer noopener">site da BitNami</a>.

Encontre o instalador que você acabou de baixar (o nome do arquivo será semelhante a bitnami-joomla-VERSAO-linux-installer.run). Dê um duplo clique no ícone para iniciar o instalador.

Se você estiver usando Linux, precisará dar permissões de execução ao arquivo primeiro, usando este comando:

chmod +x /path/to/bitnami-joomla-VERSAO-linux-installer.run

<img src="https://docs.joomla.org/images/a/a0/Joomla_welcome2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Configuração do lampstack Joomla Bitnami" />

Clique em "Avançar".

<img src="https://docs.joomla.org/images/5/5f/Joomla_components2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Componentes do lampstack Joomla Bitnami" />

Selecione os componentes que você deseja instalar. Se não tiver certeza, deixe os componentes padrão marcados. Clique em "Avançar" quando terminar.

<img src="https://docs.joomla.org/images/0/0a/Joomla_directory2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Diretório de instalação do lampstack Joomla Bitnami" />

Agora será perguntado onde você deseja instalar o programa. Forneça o local onde você deseja instalar o stack do Joomla! da BitNami e clique em "Avançar" quando terminar.

<img src="https://docs.joomla.org/images/3/3c/Joomla_userdata2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Conta admin do lampstack Joomla Bitnami" />

O usuário e senha que você fornecer aqui serão usados para criar a conta de administrador no Joomla! Clique em "Avançar" quando terminar.

<img src="https://docs.joomla.org/images/8/8b/Joomla_sitename2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Nome do site Joomla Bitnami lampstack" />

Digite o nome que deseja usar para o seu site Joomla e clique em "Avançar".

<img src="https://docs.joomla.org/images/d/dd/JoomlaReadytoinstall2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Pronto para instalar o Joomla Bitnami lampstack" />

O instalador permite que você configure uma conta de e-mail para que o Joomla! possa enviar notificações por e-mail. Clique em "Avançar".

<img src="https://docs.joomla.org/images/9/9d/JoomlaCopyingfiles2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Copiando arquivos Joomla Bitnami lampstack" />

Aguarde um momento enquanto o instalador copia os arquivos e configura a instalação do Joomla!.

<img src="https://docs.joomla.org/images/e/ea/Joomlafinalscreen2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Tela final do Joomla Bitnami lampstack" />

O Joomla! está agora configurado e pronto para ser usado. Clique em "Concluir" para iniciar o aplicativo.

<img src="https://docs.joomla.org/images/8/8d/JoomlaManager.png"
decoding="async" data-file-width="784" data-file-height="586"
width="784" height="586" alt="Gerenciar servidores do Joomla Bitnami lampstack" />

Usar a ferramenta de gerenciamento é fácil para iniciar/parar os servidores Apache e MySQL.

<img src="https://docs.joomla.org/images/7/73/Joomlaapplicationscreen2.png"
decoding="async" data-file-width="982" data-file-height="729"
width="982" height="729" alt="Tela do aplicativo Joomla" />

Você pode gerenciar o banco de dados Joomla! com o phpMyAdmin facilmente.

<img src="https://docs.joomla.org/images/f/f3/JoomlaphpMyAdmin.png"
decoding="async" data-file-width="982" data-file-height="751"
width="982" height="751" alt="Tela do phpMyAdmin" />

## Opção 2: BitNami LAMPStack e Joomla!

### O que é o BitNami LAMPStack?

O BitNami LAMPStack é um pacote gratuito e fácil de instalar que agrupa todos os softwares (dependências) necessários para configurar um ambiente LAMP (Apache, MySQL e PHP para Linux) pronto para desenvolvimento ou produção. Ele é autossuficiente, não faz modificações no seu sistema e pode ser desinstalado facilmente. Você pode baixar a versão mais recente do BitNami LAMPStack para Linux em <a href="http://bitnami.org/stack/lampstack" rel="nofollow noreferrer noopener">http://bitnami.org/stack/lampstack</a>. Também está disponível uma <a href="http://bitnami.org/stack/wampstack" rel="nofollow noreferrer noopener">versão para Windows</a> e uma <a href="http://bitnami.org/stack/mampstack" rel="nofollow noreferrer noopener">versão para OS X</a>.

Independentemente do sistema operacional que você está utilizando (Windows / Linux / Mac), o processo de instalação é o mesmo.

### Instalando o BitNami LAMPStack

Encontre o instalador que você acabou de baixar do site da BitNami (o nome do arquivo será algo semelhante a bitnami-lampstack-VERSÃO-linux-installer.run). Dê um duplo clique no ícone para iniciar o instalador.

<img src="https://docs.joomla.org/images/1/14/Lampstack_welcome.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bem-vindo ao Bitnami lampstack" />

Clique em "Avançar".

<img src="https://docs.joomla.org/images/7/78/Lampstack_directory.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Diretório do Bitnami lampstack" />

Agora será perguntado onde você deseja instalar o programa. Selecione o local na sua máquina e clique em "Avançar" quando terminar.

<img src="https://docs.joomla.org/images/2/22/Lampstack_passwd.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Senha do Bitnami lampstack" />

Digite a senha root do MySQL. Esta será a senha para o usuário "root" do banco de dados.

<img src="https://docs.joomla.org/images/7/72/LampstackReadytoinstall.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Pronto para instalar o Bitnami lampstack" />

O instalador agora está pronto para iniciar o processo de instalação. Clique em "Avançar".

<img src="https://docs.joomla.org/images/1/19/LampstackCopyingfiles.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Copiando arquivos do Bitnami lampstack" />

Aguarde um momento enquanto o instalador copia os arquivos e configura sua instalação LAMPStack.

<img src="https://docs.joomla.org/images/b/bc/Lampstackfinalscreen.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Tela final do Bitnami lampstack" />

O BitNami LAMPStack agora está configurado e pronto para ser usado. Clique em "Concluir" para iniciar a aplicação.

### Instalando o Joomla! manualmente

Siga as instruções descritas no artigo Instalando Joomla.

*Traduzido por openai.com*

