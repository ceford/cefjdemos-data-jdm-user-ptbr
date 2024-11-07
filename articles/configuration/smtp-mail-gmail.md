<!-- Filename: How_to_debug_SMTP_mail_in_Joomla_4 / Display title: SMTP e Gmail -->

## Introdução

Na página de Configuração Global, painel do Servidor, há uma opção para selecionar um agente de entrega de e-mail. A configuração padrão é *PHP Mail*. Se isso não funcionar, pode ser recomendado usar SMTP. Ele usa o mesmo mecanismo do seu aplicativo de e-mail. Há várias configurações que você precisa acertar. Resumidamente:

Vá para **Configuração Global** e selecione a aba **Servidor**. Procure pelo painel de *E-mail* próximo ao final do formulário.

- **Mailer** definido para SMTP. Vários outros campos surgirão.
- **Host SMTP** Por padrão, é localhost, mas é improvável que isso funcione. Precisa ser definido para o host que gerencia seu e-mail de saída, por exemplo, uma conta do Gmail.
- **Porta SMTP** O padrão é 25. Verifique se esse é o valor que seu Host SMTP espera.
- **Segurança SMTP** O padrão é *Nenhum*, mas você provavelmente precisará de STARTTLS.
- **Autenticação SMTP** Isso pode não ser necessário se você estiver usando uma rede doméstica que espera que e-mails de saída não exijam autenticação. Caso contrário:
- **Nome de usuário SMTP** e **Senha SMTP** insira os valores que você usa para acessar sua conta de e-mail pela internet.
- Selecione o botão **Enviar E-mail de Teste**.

## Usando o Gmail

Se você tiver uma conta do Gmail funcionando, poderá usar o Gmail como seu servidor de e-mails configurando-o na configuração global.

Na aba do servidor, defina o seguinte:

- Mailer: SMTP
- SMTP Host: smtp.gmail.com
- SMTP Porta 465
- Segurança SMTP: SSL/TLS
- Autenticação SMTP: Sim
- Preencha as próximas duas linhas com suas informações. Você precisa usar uma senha específica para aplicativos (ASP), descrita abaixo.
- Nome de usuário SMTP: seu nome de usuário do Gmail
- Senha SMTP: a senha específica para aplicativo (ASP) que você gerou, descrita abaixo.

As seguintes combinações também funcionam:

- SMTP Porta 587
- Segurança SMTP: STARTTLS
- SMTP Porta 25
- Segurança SMTP: STARTTLS

O módulo SSL não precisa estar habilitado no Apache.

A extensão OpenSSL precisa estar habilitada no PHP. Os detalhes podem ser encontrados na [página de Instalação do php.net](https://www.php.net/manual/pt_BR/openssl.installation.php).

Se você estiver usando WAMP no Windows, o módulo openssl não está habilitado por padrão, e você precisa habilitá-lo. Para fazer isso:

1. Abra o arquivo php.ini e descomente a linha `extension=php_openssl.dll` removendo o ponto e vírgula (;) do início da linha.
2. Salve o arquivo php.ini e reinicie o serviço Apache.

Observe que se você usar a verificação em 2 etapas no Gmail, precisará adicionar uma nova senha em Configurações - Contas - Alterar configurações de contas - Outras configurações da Conta Google - Segurança - Verificação em 2 etapas - Gerenciar suas senhas específicas de aplicativo.

Quando a nova Senha Específica para Aplicativo (ASP) for apresentada em grupos de quatro caracteres separados por espaços, certifique-se de que você **NÃO insira os espaços** na senha SMTP nas configurações do servidor de e-mail no Joomla.

- Senhas Específicas para Aplicativo (ASPs): Veja a página de Suporte do Google intitulada [Fazer login com Senhas de Aplicativos](https://support.google.com/accounts/answer/185833).
- Verificação em 2 etapas: Veja a página de Suporte do Google intitulada [Ativar Verificação em 2 etapas](https://support.google.com/accounts/answer/185839).

## Depuração

Se o e-mail não for enviado ou nunca chegar:

- Selecione **Plugins** no **Painel Inicial → Painel do Site**.
- Encontre e ative o plugin **System - Debug** e configure-o:
- Defina **Grupos Permitidos** para *Super Usuários* para restringir a saída de depuração à sua própria sessão de login, tanto no back-end quanto no front-end. Se você não quiser fazer login no front-end como Super Usuário, crie um grupo de usuários exclusivo para suas atividades de teste e selecione esse grupo de usuários na lista de grupos de usuários permitidos.
- **Salvar e Fechar**
- Selecione **Configuração Global** no **Painel Inicial → Painel do Site**.
- Na aba *Sistema*, defina **Sistema de Depuração** como *Sim*.
- Na aba *Servidor*, defina **Relatório de Erros** como *Máximo*.
- Na aba *Logging*, anote o conteúdo de *Caminho para a Pasta de Logs*, geralmente *[algo]/administrator/logs*.
- Defina **Registrar Quase Tudo** como *Sim*.
- No painel *Registro Personalizado*, defina o campo *Categorias de Logging* para *mail* (sem aspas).
- **Salvar** para salvar as configurações de depuração.
- Na aba **Servidor**, selecione o botão *Enviar E-mail de Teste* na parte inferior da página.

Se houver problemas no código durante o teste, você deve obter um *Rastreamento de Pilha* que ajudará você ou outros a diagnosticar o problema. Além disso, procure um arquivo na pasta de logs com um nome como *administrator/logs/everything.php* e abra-o com um editor de texto. Isso pode ajudar a ver o que foi registrado quando a mensagem foi enviada.

*Traduzido por openai.com*

