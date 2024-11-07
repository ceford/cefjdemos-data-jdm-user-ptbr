<!-- Filename: How_do_you_password_protect_directories_using_htaccess%3F / Display title: Proteger Diretórios com Senha -->

## Introdução

Você pode querer proteger um diretório ou um site inteiro do acesso público. Um motivo para isso é negar o acesso público a um site de Desenvolvimento. Somente aqueles que conhecem o nome de usuário e a senha terão acesso concedido. Outro motivo é a paranoia - por exemplo, a proteção da pasta do administrador, para que os usuários tenham que inserir um nome de usuário e uma senha apenas para acessar o formulário de login do Administrador do Joomla.

O método descrito aqui é para servidores Apache usando um arquivo *.htaccess*.

### Advertência do Apache.org

A autenticação básica não deve ser considerada segura para qualquer definição particularmente rigorosa de segurança. Embora a senha seja armazenada no servidor em formato criptografado, ela pode ser enviada do cliente para o servidor em texto plano através da rede. Qualquer pessoa que estiver escutando com algum tipo de analisador de pacotes poderá ler o nome de usuário e a senha à medida que são transmitidos.

O nome de usuário e a senha são enviados com cada solicitação, não apenas quando o usuário os digita pela primeira vez. Portanto, o analisador de pacotes não precisa estar escutando em um momento particularmente estratégico, mas apenas por tempo suficiente para ver qualquer solicitação única atravessar a rede.

Além disso, o próprio conteúdo também é transmitido pela rede de forma clara e, portanto, se o site contiver informações sensíveis, o mesmo analisador de pacotes terá acesso a essas informações, mesmo que o nome de usuário e a senha não tenham sido usados para obter acesso direto ao site.

Não use autenticação básica para nada que exija segurança real. Isso é um detrimento para a maioria dos usuários, já que poucas pessoas vão se dar ao trabalho, ou ter o software ou equipamento necessário, para descobrir senhas. No entanto, se alguém tiver o desejo de invadir, pouco será necessário para que essa pessoa o faça.

A autenticação básica através de uma conexão SSL, no entanto, será segura, uma vez que tudo será criptografado, incluindo o nome de usuário e a senha.

## Usando o cPanel

Se você estiver utilizando um serviço de hospedagem, deve usar o método dele para proteção de diretórios. Por exemplo, o cPanel tem uma opção chamada Privacidade de Diretórios. Ao selecioná-la, você poderá navegar até qualquer diretório e definir um nome para ele. Você terá, então, a oportunidade de criar um Nome de Usuário e uma Senha para o diretório nomeado. Simples?

Se agora você olhar no diretório que protegeu, encontrará um novo arquivo .htaccess contendo algo como a seguinte configuração para proteger a pasta api do Joomla:

```
#----------------------------------------------------------------cp:ppd
# Seção gerida pelo cPanel: Diretórios Protegidos por Senha     -cp:ppd
# - Não edite esta seção do arquivo htaccess!                   -cp:ppd
#----------------------------------------------------------------cp:ppd
AuthType Basic
AuthName "API"
AuthUserFile "/home/nomeusuario/.htpasswds/public_html/[jroot]/api/passwd"
Require valid-user
#----------------------------------------------------------------cp:ppd
# Fim da seção gerida pelo cPanel: Diretórios Protegidos por Senha -cp:ppd
#----------------------------------------------------------------cp:ppd
```
É importante estar ciente de que a proteção de diretório do cPanel pode usar o mesmo arquivo .htaccess que está sendo usado pelo Joomla para outros propósitos.

Se você olhar no arquivo de senha citado, verá o Nome de Usuário que forneceu e a versão criptografada da senha.

A proteção pode ser removida repetindo o processo e desmarcando a caixa de seleção `Proteger este diretório por senha`. Isso remove a seção de autenticação do arquivo .htaccess, mas não remove o arquivo .htaccess!

## Regras do .htaccess

Você pode executar todas as etapas necessárias manualmente. Esta ferramenta pode ajudar:

<a href="https://www.htaccessredirect.net/" rel="nofollow noreferrer noopener"><em>Gerador de .htaccess</em></a>

Ele cria os arquivos necessários para você. Você precisa especificar o nome de usuário,
senha e caminho.

Preencha as duas seções: **Arquivo de Proteção por Senha** e **Gerador de htpasswd** e então selecione o botão `Gerar Código`. Você receberá de volta o texto para o arquivo .htaccess e o texto para o arquivo .htpasswd em caixas separadas.
Exemplos:
```
//Arquivo de Proteção por Senha
<Files /admin>
AuthName "Prompt"
AuthType Basic
AuthUserFile /home/user/.htpasswd
Require valid-user
</Files>
```

```
John:$apr1$a3dbt6j7$KJQr137CY9QuN6tYl6M4Z1
```

*Traduzido por openai.com*

