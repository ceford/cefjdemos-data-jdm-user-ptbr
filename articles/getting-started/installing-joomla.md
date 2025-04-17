<!-- Filename: J4.x:Installing_Joomla / Display title: Instalando o Joomla -->

## Introdução

Instalar o Joomla! pela primeira vez é muito fácil. Após completar os passos preliminares, configurar um ambiente de hospedagem e criar um banco de dados, o instalador web embutido do Joomla configurará seu novo site em apenas alguns minutos. Os passos anteriores:

### Configuração de Hospedagem

Se você ainda não configurou um ambiente de hospedagem, precisa fazê-lo agora, seja em um serviço de hospedagem ou em seu computador local.

Além disso, há algumas configurações de PHP que precisam ser suficientes para o Joomla instalar. As configurações geralmente estão em um arquivo de configuração *php.ini* ou *user.ini* no servidor. Se você estiver usando hospedagem compartilhada, converse com seu serviço de hospedagem sobre como alterar essas configurações, se for possível fazê-lo. Se estiver trabalhando em um localhost, por exemplo com XAMPP, ou em um VPS ou host dedicado, você não deve ser restringido por essas configurações e pode defini-las você mesmo.

Os valores mínimos para o arquivo *php.ini* estão mostrados abaixo:

- *memory_limit:* 256M
- *upload_max_filesize:* 64M
- *post_max_size:* 64M
- *max_execution_time:* 30

É possível trabalhar com valores menores para upload_max_filesize e post_max_size, mas extensões maiores falharão ao carregar e causarão problemas imprevisíveis.

### Configuração de Banco de Dados

Se você ainda não configurou um banco de dados, faça isso agora. Isso é abordado para um serviço de hospedagem com cPanel no tutorial [Hospedagem cPanel](jdocmanual?article=user/hosting/cpanel-hosting). Há também um tutorial *Criando um Banco de Dados para Joomla!* que cobre métodos de localhost e phpMyAdmin.

Você precisará anotar informações básicas do banco de dados necessárias quando a instalação do Joomla for iniciada.

- Localização do banco de dados, geralmente *localhost* mesmo em um serviço de hospedagem. Pode ser o servidor específico de um host como *`dbserver1.yourhost.com`*.
- O nome do banco de dados
- O nome do usuário do banco de dados
- A senha do usuário do banco de dados

## Preparar para Instalação

### Baixando e Enviando Arquivos do Pacote Joomla!

Baixe a versão atual do Joomla! a partir do link na página de
[Download Joomla](https://downloads.joomla.org/).

Mova o arquivo zip do pacote de instalação do Joomla baixado para o servidor.
Para um serviço de hospedagem, você pode usar a função de Upload do Gerenciador de Arquivos do cPanel ou pode usar um Cliente FTP para transferir o arquivo zip do Joomla 5.x para o seu servidor. Há vários clientes FTP disponíveis.
Aqui está uma [Comparação de softwares de cliente FTP](https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software) detalhada.
Se estiver em dúvida, use o FileZilla.

Pasta *root* do Seu Servidor

É melhor mover o pacote zip baixado para o seu servidor e descompactá-lo lá, do que descompactar localmente e mover a árvore de arquivos depois.
Normalmente, você faz o upload de seus arquivos web para a pasta raiz do seu serviço de hospedagem.
Ela é geralmente chamada `public_html`, mas outras variações incluem `htdocs`, e isso depende de como seu anfitrião configurou o servidor. Para os propósitos do Joomla, você pode carregar os arquivos diretamente em *public_html* ou em uma subpasta que você criou dentro dela.

**Aviso:** Se você descompactar os arquivos no seu próprio computador e depois copiá-los para seu servidor, certifique-se de mover apenas as pastas e arquivos contidos **dentro** do pacote Joomla. Se você descompactar as pastas e arquivos em uma pasta, por exemplo, chamada *`Joomla`* e depois enviar essa pasta, seu site terá que ser acessado em *`seudominio.com/Joomla`* ao invés de *`seudominio.com`*. Você pode renomear o subdiretório de Joomla para algo mais apropriado para o site, como jblog, e você pode achar isso conveniente. **Nota:** os nomes de diretório devem estar em letras minúsculas, sem espaços, e usar traços ao invés de sublinhados para separar as palavras.

Os arquivos do pacote zip podem ser extraídos diretamente no host usando várias ferramentas de linha de comando (por exemplo, unzip), que precisam estar instaladas no servidor. Se o seu serviço de hospedagem usa a ferramenta de administração cPanel, o botão Extrair pode ser pressionado no Gerenciador de Arquivos. Além disso, a ferramenta gratuita de terceiros Akeeba Kickstart também pode ser usada para este propósito. Os arquivos e diretórios descompactados serão colocados na pasta atual. A extração no seu computador local depende do seu sistema operacional. Tente clicar com o botão direito e veja se há um menu de extração. Nesse caso, seu sistema operacional pode colocar os arquivos em uma pasta com o mesmo nome do arquivo zip. Após a extração, você pode excluir o arquivo zip e renomear a pasta de extração para algo curto e adequado para uso em uma URL.

## Iniciar Instalação

Com os requisitos acima atendidos, um banco de dados criado e os arquivos necessários do Joomla no lugar, você está pronto para instalar o Joomla. Inicie o instalador web do Joomla abrindo seu navegador favorito e acessando o nome de domínio do site. Em uma instalação em hospedagem, você usará *`https://www.seusitenome.com`*. Se você estiver instalando o Joomla localmente, usará *`http://localhost/`* e deverá ver a tela de instalação.

![Instalador do Joomla parte 1, idioma de instalação e nome do site](../../../en/images/getting-started/installing-joomla-installer-1.png)

O Joomla tentará identificar o campo *Selecionar Idioma* automaticamente a partir do idioma do seu navegador. Você pode alterar isso, se necessário.

Preencha as seguintes informações.

- **Nome do Site** O nome do seu site – isso pode ser alterado a qualquer momento na página de Configuração Global do Site.

Quando tudo na primeira página estiver completo, clique no botão *Configurar Dados de Login* para continuar.


## Dados de Login

Agora você deve ver a tela de dados de login.

![Joomla instalador parte 2, dados de login](../../../en/images/getting-started/installing-joomla-installer-2.png)

Preencha as seguintes informações.

- **Nome Real** O nome do Super Usuário. É assim que o Joomla irá
  cumprimentá-lo quando você fizer login.
- **Nome de usuário da conta de Super Usuário** O nome de usuário para o *Super Usuário*.
  Evite usar *admin* como nome de Administrador!
- **Senha de Administrador** Lembre-se de que um Super Usuário tem controle máximo das
  interfaces do Site e do Administrador, então use uma senha difícil.
  Use **Meu Perfil** na interface de *Administração* para alterá-la mais tarde.
- **Endereço de Email do Super Usuário** O endereço de email do Super Usuário. Insira um
  email válido caso esqueça sua senha. Este é o endereço de email
  onde você receberá um link para alterar a senha do Super Usuário.

Quando tudo na segunda página estiver concluído, clique no botão *Configurar Conexão com o Banco de Dados* para continuar.

## Configuração do Banco de Dados

Insira as informações do banco de dados anotadas quando você criou o banco
para esta instalação.

![Instalador Joomla parte 3, configuração do banco de dados](../../../en/images/getting-started/installing-joomla-installer-3.png)

Para simplificação, estas instruções são uma referência para instalar
com um banco de dados MySQLi. As instruções na página de instalação são autoexplicativas, mas aqui estão novamente:

- **Tipo de Banco de Dados** MySQLi é o banco de dados comum usado
- **Nome do Host** Onde seu banco de dados está localizado. Comum é *localhost*,
  mesmo em serviços de hospedagem. No entanto, alguns hosts usam um servidor de base de dados específico, como *dbserver1.yourhost.com*.
- **Nome de Usuário** O nome de usuário usado para conectar ao banco de dados
- **Senha** A senha para o usuário do banco de dados (não a sua senha de Administrador)
- **Nome do Banco de Dados** O nome do banco
- **Prefixo das Tabelas** Este é gerado automaticamente como uma característica de segurança. Você pode aceitar o padrão gerado aleatoriamente ou alterá-lo. Apenas não esqueça de colocar o caractere underline (`_`) no final do prefixo.
- **Criptografia da Conexão** especifica como a conexão com o
  banco de dados deve ser criptografada. Se você não souber, é melhor
  manter o padrão. No entanto, isso permite que empresas que usam autenticação de uma ou duas vias para a conexão do banco de dados forneçam isso.

Todas essas escolhas e mais podem ser editadas na página de Configuração Global do Site, em *Opções do Servidor* após a conclusão da instalação. Note que você quebrará sua instalação se alterar essas configurações após a instalação, a menos que tenha uma cópia completa do banco de dados atual sendo usado pela instalação do Joomla. Usos comuns seriam atualizar o nome de usuário e a senha do banco de dados ou completar a transferência de uma instalação existente para um novo host com parâmetros diferentes.

Após clicar no botão *Instalar Joomla*, você deve ver a barra de progresso da instalação Joomla.

![Instalador Joomla parte 4, barra de progresso da instalação](../../../en/images/getting-started/installing-joomla-installer-4.png)

Uma vez que a instalação seja concluída, você deve ver a página de sucesso.

## Finalizando

### Sucesso e Finalizando a Instalação

Parabéns! Seu site Joomla está pronto.

![Instalador do Joomla parte 5, seu site joomla está pronto](../../../en/images/getting-started/installing-joomla-installer-5.png)

A captura de tela acima mostra uma instalação de desenvolvedor. Uma instalação de produção remove automaticamente a pasta de Instalação.

Se você deseja começar a usar o Joomla imediatamente sem instalar idiomas adicionais, você pode selecionar *Abrir Administrador* para ir ao *Painel Administrativo* ou selecionar *Abrir Site* para ir à página inicial do site. Você pode ver uma seção com configurações recomendadas de PHP.

- **Configurações Recomendadas** Estas configurações são recomendadas na sua configuração PHP, mas não impedirão a instalação do Joomla!. Você pode se referir às instruções acima sobre como elas podem ser alteradas, se houver necessidade.

### Idiomas Adicionais

Como parte do processo de instalação do Joomla, você tem a oportunidade de instalar idiomas adicionais antes de concluir a instalação.

Para fazer isso, selecione o botão Instalar Idiomas Adicionais.

Isso o levará a uma página de instalação extra que permite selecionar os idiomas necessários.

#### Instalar Idiomas Adicionais

É exibida uma lista de pacotes de idiomas.

![Instalador do Joomla parte 6, instalar idiomas adicionais](../../../en/images/getting-started/installing-joomla-installer-6.png)

Selecione até 3 idiomas que você deseja instalar. (Mais de 3 de uma vez podem causar problemas de tempo de espera; você pode instalar mais posteriormente.)

Lembre-se do seguinte:

- Os pacotes de idiomas incluídos nas distribuições personalizadas não serão listados nesta etapa, pois já estão instalados.
- Uma versão dos pacotes propostos corresponderá à versão principal do Joomla (5.0.x, 5.1.x, etc.). A versão secundária do pacote pode não corresponder, por exemplo, você está instalando a versão 5.0.3 e é mostrado um pacote de idiomas 5.0.2.
- Pacotes de idiomas não correspondentes no exemplo acima podem ter strings não traduzidas.
- Os pacotes de idiomas não correspondentes serão oferecidos como uma atualização quando os pacotes forem atualizados pelas equipes de Tradução registradas. A atualização disponível será mostrada no Painel de Controle, bem como em **Extensões → Atualizar**. Esse comportamento é semelhante a **Extensões → Instalar Idiomas**.

*Próximo* e uma barra de progresso serão exibidos enquanto o(s) pacote(s) de idioma(s) estão sendo instalados.

#### Escolher o Idioma Padrão

Quando a instalação dos idiomas for concluída, você verá agora uma tela semelhante a *Parabéns! Seu site Joomla está pronto.*. A diferença será uma lista dos idiomas instalados permitindo que você selecione o idioma padrão para o site e a interface do administrador.

![Instalador do Joomla parte 7, escolha o idioma padrão](../../../en/images/getting-started/installing-joomla-installer-7.png)

- Selecione o idioma padrão que deseja usar.
- Quando você tiver selecionado o idioma padrão, clique no botão *Definir idioma padrão* para confirmar.
- Uma mensagem do sistema será exibida confirmando que o Joomla configurou o idioma padrão do ADMINISTRADOR e do SITE. Essa mensagem pode ser fechada.

#### Finalizar

Agora você pode navegar até o *Painel Administrativo*. Faça login selecionando *Abrir Administrador* ou vá diretamente para a página inicial do seu site selecionando *Abrir Site*.

