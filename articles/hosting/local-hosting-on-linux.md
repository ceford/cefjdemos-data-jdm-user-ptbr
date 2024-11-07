<!-- Filename: No_original_yet / Display title: Hospedagem Local no Linux -->

## Introdução

Este artigo aborda a hospedagem do Joomla em um computador pessoal baseado em Linux para fins de teste e desenvolvimento. As versões do Linux abordadas são da família Debian-Ubuntu, especificamente o Linux Mint. Outras distribuições são semelhantes, mas possuem sintaxes de comando e locais de arquivos diferentes.

Você precisa instalar um conjunto de pacotes de software frequentemente chamado de stack LAMP. As letras referem-se a Linux, Apache, MySQL e PHP. Você pode instalar o software usando a Interface Gráfica do Usuário (GUI) ou a linha de comando em uma janela do Terminal. Elas são diferentes maneiras de usar o Gerenciador de Pacotes Synaptic.

## Instalar o Apache com a GUI

No Menu do sistema, marcado com o logotipo do LM, selecione Administração / Gerenciador de Pacotes Synaptic. Você será solicitado a inserir sua senha. Digite sua senha de login para abrir a GUI. No canto superior direito, há um botão de `Pesquisa`. Selecione-o, digite **apache** e clique em `Pesquisar`. Marque a caixa de seleção `apache2` e, no rótulo pop-up, escolha `Marcar para Instalação`. Outro pop-up mostrará uma lista de pacotes adicionais necessários para dar suporte ao apache. Selecione `Marcar`:

![gerenciador de pacotes synaptic](../../../en/images/hosting/synaptic-package-manager-gui.png "Interface do Gerenciador de Pacotes Synaptic")

Selecione o botão `Aplicar` na barra de ferramentas superior e, em seguida, o botão `Aplicar` na caixa de diálogo Resumo. O Apache será instalado e configurado, e o processo terminará com uma **caixa de diálogo de Alterações Aplicadas**. Selecione `Fechar`.

Você pode confirmar que o Apache está instalado e funcionando ao abrir seu navegador — Firefox, por padrão, em uma nova instalação do Linux Mint — e digitar **localhost** na barra de URL. Você deve ver a Página Padrão do Ubuntu Apache2:

![página padrão do apache](../../../en/images/hosting/apache-default-page.png "Página Padrão do Apache")

A página contém algumas informações úteis sobre localizações de arquivos que podem não estar tão prontamente disponíveis mais tarde, então você pode querer imprimir esta página em papel ou em um arquivo PDF.

## Instalar PHP com a CLI

É provavelmente melhor instalar o PHP usando a linha de comando. Uma das razões para isso é que, no momento em que este texto foi escrito, o Gerenciador de Pacotes Synaptic oferece apenas o PHP8.1, embora o PHP8.2 esteja disponível há algum tempo e possa ser instalado a partir de um repositório de terceiros. Há uma boa descrição do procedimento neste tutorial com seções de Início Rápido e Detalhado.

Primeiro, feche a interface gráfica do Gerenciador de Pacotes Synaptic e depois abra uma janela do Terminal e insira os seguintes comandos, um de cada vez:

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.2 php8.2-cli php8.2-{bz2,curl,mbstring,intl}
sudo apt install php8.2-fpm
sudo a2enconf php8.2-fpm
sudo systemctl reload apache2
```
Em seu navegador, verifique se a página padrão do localhost ainda está funcionando.

## Instalar MySQL ou MariaDb

Você pode procurar na internet informações sobre cada um desses pacotes de banco de dados. MySQL é a escolha tradicional, mas foi adquirido pela Oracle e agora é menos popular. MariaDB é uma substituição Open Source direta com recursos adicionais. Ambos funcionam com o Joomla! 5, mas não é fácil mudar de um para o outro. As tabelas precisam ser exportadas e importadas. O Joomla! 5 requer versões mínimas específicas que o Linux Mint oferece via o Gerenciador de Pacotes Synaptic.

Abra a interface gráfica do Gerenciador de Pacotes Synaptic e procure por mysql-server ou mariadb-server. Selecione a caixa de seleção para o item que termina em -server. Selecione `Marcar para Instalação` e depois `Aplicar` na Barra de Ferramentas superior. Você pode abrir o painel de Detalhes para ver o que está acontecendo durante a instalação. Selecione `Fechar` quando terminar.

Você pode testar se o seu banco de dados está funcionando digitando `mysql` na linha de comando. Isso é o mesmo tanto para MySQL quanto para MariaDB. Você deverá ver uma mensagem de erro `Acesso negado`, o que está certo, pois indica que a instalação do seu banco de dados está realmente funcionando.

## Instalar o phpMyAdmin

phpMyAdmin é uma ferramenta de gerenciamento de banco de dados com interface gráfica que você precisará para criar e gerenciar seus bancos de dados. No gerenciador de pacotes Synaptic, procure por **phpmyadmin**. Selecione a caixa de seleção e marque `Marcar para Instalação`. Após o download, haverá um aviso para selecionar o `Servidor Web para reconfiguração automática`. Marque a caixa de seleção `apache2` e em seguida o botão `Próximo`. Na próxima tela de configuração, deixe marcada a caixa `Configurar banco de dados...` e selecione `Próximo`.

Escolha uma senha para o usuário phpmyadmin. Teste: no seu navegador, digite localhost/phpmyadmin na barra de URL. Você deverá ver a tela de login do phpMyAdmin. Com o nome de usuário phpmyadmin e a senha que você inseriu durante a instalação, você conseguirá fazer login. Mas você não poderá criar nenhum banco de dados! Para resolver o problema, você precisa editar o arquivo de configuração como root na janela do Terminal:

```bash
sudo nano /etc/phpmyadmin/config.inc.php
```
Encontre as duas linhas contendo // $cfg['Servers'][$i]['AllowNoPassword'] = TRUE; e remova as barras iniciais para descomentá-las. Ambas!

Então, faça login no MySQL a partir da linha de comando e crie um novo usuário, concedendo a esse usuário todos os privilégios:
```bash
sudo mysql
CREATE USER 'admin'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;
exit
```
Em seguida, volte para o phpMyAdmin e tente fazer login com o nome de usuário **admin** e nenhuma senha. Você deverá ver todos os bancos de dados e ser capaz de criar novos bancos de dados.

## Prioridade do Arquivo Índice

A localização padrão para páginas da web no Ubuntu/Linux Mint é /var/www/html. Se
você listar o conteúdo desse diretório, verá que ele contém index.html
com o conteúdo da Página Padrão do Ubuntu Apache2. Crie um arquivo chamado
index.php nesse diretório com o seguinte conteúdo:

```php
<?php echo phpinfo();
```
Recarregue o localhost. Não há mudança! Digite **localhost/index.php** na
barra de URL e você verá uma página contendo informações da versão do PHP. Este
comportamento é controlado pela configuração padrão do Apache, que pode ser
alterada habilitando o módulo `dir` do Apache e editando sua configuração:

```bash
sudo a2enmod dir
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Mova index.php para o início da lista. Em seguida, reinicie o Apache:

```bash
sudo systemctl restart apache2
```

Desta vez, usando apenas **localhost** na barra de URL, você deve ver o conteúdo
do arquivo index.php, uma página de Informações do PHP.

## Hosts Virtuais

Em uma instalação padrão do Linux, os arquivos do sistema estão na pasta root (/)
e os arquivos de dados do usuário estão na pasta home (/home/meunomeusuario). Isso é
um problema potencial porque o usuário padrão do Apache, www-data, pode não ter permissões
adequadas para criar arquivos no espaço de arquivos do usuário. A melhor solução é criar
Hosts Virtuais.

Primeiro, é necessário um módulo que permita ao Apache alternar seu usuário e grupo para
adequar-se a cada usuário:

```bash
sudo apt-get install libapache2-mpm-itk
sudo a2enmod mpm_itk
```

Em seguida, faça uma cópia do arquivo de configuração do site padrão e edite-o:

```bash
cd /etc/apache2/sites-available
sudo cp 000-default.conf meunomeusuario.localhost.conf
sudo nano meunomeusuario.localhost.conf
```

O arquivo de configuração do site padrão contém comentários para explicar seu
conteúdo. Eles são omitidos na ilustração abaixo. Descomente a linha ServerName e troque todas
as instâncias de `meunomeusuario` para o seu próprio nome de usuário.

```xml
<VirtualHost *:80>
        ServerName meunomeusuario.localhost
        ServerAdmin webmaster@localhost
        DocumentRoot /home/meunomeusuario/public_html
        <IfModule mpm_itk_module>
                AssignUserId meunomeusuario meunomeusuario
        </IfModule>
        <Directory /home/meunomeusuario/public_html/ >
                Options Indexes FollowSymLinks
                AllowOverride None
                Require all granted
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Habilite o novo site e reinicie o Apache:

```bash
sudo a2ensite meunomeusuario.localhost
sudo systemctl reload apache
```

Faça uma entrada no arquivo /etc/hosts para adicionar uma entrada para o novo host virtual.
Caso contrário, seu navegador procurará por ele na internet.

```bash
sudo nano /etc/hosts
```

Quando terminar, ficará algo assim:

```bash
127.0.0.1       localhost
127.0.0.1       meunomeusuario.localhost
127.0.1.1       nome-do-host

# As seguintes linhas são desejáveis para hosts compatíveis com IPv6
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
**Nome-do-Host:** Este é o nome que você deu ao seu computador quando instalou
o Linux. Você precisará dele em breve. Pode alterá-lo se desejar - mas é melhor
ler sobre isso e fazê-lo primeiro.

Tudo estando bem, com uma URL do tipo meunomeusuario.localhost você verá uma
listagem de diretório do seu diretório public_html. A exibição pública de listagens
de diretórios é considerada uma má prática, um risco de segurança, e geralmente é
proibida por outra configuração do Apache. No entanto, para um site pessoal em um
computador pessoal usado para desenvolvimento e testes, é muito útil. Muitos
sites diferentes podem ser configurados em diferentes subdiretórios. Por exemplo,
sites Joomla 4 e Joomla 5, Fóruns, Wikis e assim por diante. Quando você tem
muitos sites de teste, é difícil lembrar todos os nomes dos subdiretórios!

## Acesso à Rede Doméstica

Se você tem outro computador na sua rede doméstica, provavelmente gostaria de acessar seu site Linux a partir dele também. Para que isso funcione, você precisa de outro host virtual. Copie e edite o que você acabou de criar:

```bash
cd /etc/apache2/sites-available
sudo cp username.localhost.conf username.conf
sudo nano username.conf
```
Altere o ServerName de username.localhost para username.hostname e, em seguida, habilite o novo site virtual e reinicie o Apache.

```bash
sudo a2ensite username
sudo apachectl restart
```
Vá para o seu outro computador na rede doméstica e edite seu arquivo pessoal de hosts. Por exemplo, em um Mac, edite /private/etc/hosts e adicione a seguinte linha no final:

```bash
192.168.178.20 username.hostname www.username.hostname
```
Onde 192.168.178.20 é o endereço IP do seu computador Linux.

Agora, no seu segundo computador, você deve ser capaz de acessar o servidor web no seu computador Linux digitando username.hostname na barra de URL do seu navegador.

## Notas sobre Partições

O software instalado usando o Gerenciador de Pacotes Synaptic geralmente se encontra no diretório raiz do Linux (/). Os dados dos usuários estão localizados no diretório home (/home). Em uma instalação simples, esses diretórios estão na mesma partição física de disco.

Em uma instalação mais complexa, talvez com a opção de inicializar diferentes sistemas operacionais (Windows ou Linux) ou diferentes versões do mesmo sistema operacional, o diretório raiz e os dados dos usuários costumam estar em partições separadas. Isso permite acesso aos mesmos dados de usuário a partir de cada sistema operacional.

Há uma complicação: um site Joomla localizado em um diretório /home/nome_de_usuario precisa de dados de banco de dados que normalmente estão no diretório raiz, especificamente em /var/lib/mysql. Você pode mover o diretório de dados do MySQL/MariaDB para um local acessível por ambos os sistemas operacionais, seja na partição /home ou em uma partição separada. Este tutorial descreve como Mudar o Diretório de Dados do MySQL no Ubuntu e Debian Linux. Isso precisa ser feito para cada sistema operacional, mas não é abordado aqui.

*Traduzido por openai.com*

