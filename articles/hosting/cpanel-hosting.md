<!-- Filename: J4.x:Hosting_Setup / Display title: Hospedagem cPanel -->

## Introdução

## Hospedagem cPanel

Quando você faz login no seu serviço de hospedagem cPanel, é isso que você deve esperar ver:

![painel de controle de hospedagem cpanel](../../../en/images/hosting/cpanel-hosting.png)

### Configuração de Banco de Dados

O painel de Bancos de Dados é usado para criar um banco de dados e um usuário de banco de dados para o Joomla.

Selecione o item MySQL Databases e insira um nome para o banco de dados no formulário. A primeira parte do formulário é predefinida. O resto depende de você. Deve ser curto e, talvez, não óbvio - *jblog*, por exemplo.

No mesmo formulário, desça até a seção *Add New User*. Insira um nome de usuário. Pode ser qualquer coisa que você goste. Será usado no arquivo de configuração do Joomla, então não é algo que você precisa lembrar. Use o gerador de senhas para criar uma senha impossível de memorizar e copie-a para um editor de texto - você precisará dela durante a instalação do Joomla.

No mesmo formulário, desça até *Add User to Database*. Selecione o usuário que você criou e o banco de dados que você criou nas listas suspensas e, em seguida, clique no botão Add. Um formulário para Gerenciar Privilégios será aberto. Marque a caixa de seleção *All Privileges* e clique no botão *Make Changes*.

É isso - agora você tem um banco de dados pronto para uma instalação do Joomla.

### Fazer Upload do Código Fonte do Joomla

Em algum momento, você terá baixado o arquivo zip com o código fonte do Joomla para seu próprio laptop ou computador de mesa. Agora você precisa decidir como estruturar seu site. O diretório raiz de documentos do seu site é a pasta *public_html*. Você poderia colocar o Joomla lá. No entanto, isso o impede de usar outro aplicativo no mesmo site. Por exemplo, você poderia ter duas instalações separadas do Joomla, uma para produção (visualização pública) e outra para testes (visualização privada). Então, você poderia criar uma pasta dentro do *public_html*, chamada *j4*, por exemplo, e fazer o upload do Joomla lá. Você poderia ter outra pasta chamada *j4test* e colocar outra cópia do Joomla lá. A ilustração abaixo mostra tal configuração com dois sites Joomla.

![gerenciador de arquivos de hospedagem cpanel](../../../en/images/hosting/cpanel-file-manager.png)

Quando você tiver decidido sobre sua estrutura, selecione a pasta Joomla escolhida no Gerenciador de Arquivos e clique no botão Upload. No formulário de upload, selecione o arquivo zip do código fonte do Joomla no seu computador local para enviá-lo para a pasta selecionada. Após o upload, volte para o Gerenciador de Arquivos, selecione o arquivo *zip* e clique no botão Extract. Após a extração, você pode selecionar e excluir o arquivo *zip*.

É isso! Você está pronto para instalar o Joomla.

*Traduzido por openai.com*

