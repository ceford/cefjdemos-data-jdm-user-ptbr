<!-- Filename: J4.x:Privacy_Setup / Display title: Configuração de Privacidade -->

## Componente de Privacidade

O Componente de Privacidade é utilizado para gerenciar informações de privacidade, reunir solicitações de informações ou pedidos para ter informações deletadas. Ele é baseado em endereços de email, portanto, aplica-se mais obviamente a usuários registrados que devem fornecer um endereço de email durante o registro. Também se aplica a dados de usuários não registrados cujos endereços de email foram fornecidos através do componente de Contatos. Não implementa a permissão para uso de cookies ou rastreamento exigido pelo GDPR.

Quando informações pessoais identificáveis são coletadas, você deve garantir que:

- O usuário seja informado sobre o motivo pelo qual você está solicitando essas informações em uma linguagem clara e fácil de entender.
- O usuário saiba quais dados você coleta sobre ele.
- O usuário saiba para que você usará os dados.
- O usuário tenha consentido ativamente com o uso dos dados por você.

Normalmente, essas informações são descritas em um artigo de Política de Privacidade.

## Painel de Privacidade

O painel de privacidade fornece um resumo das **Solicitações de Privacidade** e do **Status de Privacidade** do site. Para acessar:

- Selecione **Usuários → Privacidade** no menu do Administrador.

![painel de privacidade](../../../en/images/privacy/privacy-dashboard.png)

Existem dois módulos exibidos por padrão no Painel de Privacidade:

### Solicitações de Privacidade

Este módulo fornece um resumo das solicitações de informação atuais.

### Status de Privacidade

Este módulo mostra o status das opções que os proprietários do site devem atender:

- **Política de Privacidade Publicada** define um artigo de Política de Privacidade no plugin **Sistema - Consentimento de Privacidade**.
- **Item de Menu de Solicitação Publicado** define um item de menu para permitir que usuários autenticados enviem solicitações.
- **Solicitações Urgentes Pendente** verifica solicitações confirmadas mais antigas que a idade especificada nos parâmetros do componente (padrão de 14 dias) e alerta o proprietário do site sobre quaisquer solicitações que necessitem de atenção urgente.
- **Envio de Email Habilitado** o site deve ser capaz de enviar e-mails para processar solicitações de informação.
- **Criptografia de Banco de Dados** isto é relevante quando um banco de dados remoto é utilizado.

## Plugin: Sistema - Consentimento de Privacidade

Se este plugin estiver desativado, o painel de Status de Privacidade do Dashboard mostrará que a Política de Privacidade está **Não Disponível** e fornecerá um link para o formulário de edição do plugin. Quando ativado, o plugin solicita que qualquer novo usuário que se registre no seu site consinta com a Política de Privacidade. Todos os usuários existentes serão redirecionados para o Perfil do Usuário para que possam consentir.

Para configurar os consentimentos:

- Selecione **Dashboard Inicial** → **Plugins** no menu do Administrador.
- Encontre o plugin **Sistema - Consentimento de Privacidade** (não confundir com o plugin Privacidade - Consentimentos).
- Selecione para abrir o formulário de entrada de dados do plugin.

![plugin sistema consentimento de privacidade](../../../en/images/privacy/plugin-system-privacy-consent.png)

- Defina o **Status** como **Ativado**.
- Opcional: Selecione ou crie um artigo para vincular a partir do formulário de Registro. Ou defina o Tipo de Privacidade para Item de Menu e Selecione ou Crie um item de menu.
- Selecione a aba **Expiração** e **Alternar Ajuda Inline** para uma explicação de cada campo. Ative e ajuste os parâmetros **se** desejar que os consentimentos expirem após um número selecionado de dias.

### Notas de Consentimento de Privacidade para sites Multilíngues:

**Mensagem Curta da Política de Privacidade e de Redirecionamento** Se você usar o texto padrão, ele será exibido no idioma do usuário. Não é possível traduzir o texto personalizado. Se você deseja personalizar o texto e exibi-lo em vários idiomas, você deve deixar este campo em branco e usar o recurso de substituição de idioma do Joomla para personalizar as strings de idioma `PLG_SYSTEM_PRIVACYCONSENT_NOTE_FIELD_DEFAULT` e `PLG_SYSTEM_PRIVACYCONSENT_REDIRECT_MESSAGE_DEFAULT` para cada idioma instalado.

**Artigo de Privacidade** e **Item de Menu de Privacidade** Se você associar este artigo ou item de menu com alternativas em outros idiomas, a política de privacidade será exibida no idioma correto para o usuário.

## Plugin: Usuário - Termos e Condições

Quando ativado, este plugin solicita que qualquer novo usuário que se registre no seu site concorde com os Termos e Condições de uso do seu site. Todos os usuários existentes serão redirecionados para seu Perfil de Usuário para que possam consentir.

Este plugin não está ativado por padrão. Para ativar:

- Selecione **Painel Inicial → Plugins** no menu do Administrador.
- Encontre o plugin **Usuário - Termos e Condições**.
- Selecione para abrir o formulário de entrada de dados do plugin.
- Defina o **Status** como **Ativado**.
- Opcional: Selecione ou Crie um artigo para vincular no formulário de Registro.

### Notas sobre Usuário - Termos e Condições para sites Multilíngues

**Termos e Condições Curtos** Se você usar o texto padrão, ele será exibido no idioma do usuário. Não é possível traduzir o texto personalizado. Se você deseja personalizar o texto e exibi-lo em vários idiomas, deve deixar este campo em branco e usar a funcionalidade de sobreposição de idioma do Joomla para personalizar as strings de idioma `PLG_USER_TERMS_NOTE_FIELD_DEFAULT` para cada idioma instalado.

**Artigo de Termos & Condições** Se você associar este artigo com alternativas em outros idiomas, a política de privacidade será exibida no idioma correto para o usuário.  

## Exibição de Consentimento de Registro de Usuário

Juntos, os dois plugins aparecem no formulário de Registro de Usuário como na captura de tela a seguir:

![visualização de consentimentos de privacidade no site](../../../en/images/privacy/privacy-consents-site.png)

## Item do Menu: Solicitação de Informações de Privacidade

Usuários registrados podem solicitar um resumo de informações ou remoção através de um item de menu. Configure da seguinte forma:

- Selecione **Menus** → **Menu Inferior** no menu de Administrador (use o menu que for mais conveniente).
- Insira um **Título** adequado, por exemplo: **Solicitação de Informações de Privacidade**.
- Use o botão **Selecionar** para abrir o diálogo popup do Tipo de Item de Menu.
- Na seção **Privacidade**, selecione o item **Criar Solicitação**.
- Defina o campo **Acesso** como **Registrado**.
- **Salvar & Fechar**.

Vá para a visualização do seu site e verifique se o item do menu não é exibido quando você não está logado e se é exibido após o login. Use o link e experimente a opção **Exportar**. Você pode experimentar a opção **Remover** mais tarde usando uma conta fictícia. Se houver uma solicitação pendente, você verá uma mensagem de erro:

“Não foi possível criar sua solicitação de informações. Já existe uma solicitação de informações ativa para este endereço de e-mail e tipo de solicitação. Por favor, entre em contato com o proprietário do site para atualizações sobre esta solicitação.”  

## Item de Menu: Solicitação de Confirmação de Privacidade

Para finalidades de SEF, você pode criar um item de menu oculto para que o usuário possa confirmar a solicitação. Isso estará no link enviado por e-mail.

- Selecione **Menus** → **Menu Oculto** no menu do Administrador (crie um menu oculto sem posição de módulo atribuída ou veja abaixo).
- Insira um **Título** apropriado, por exemplo: **Confirmar Solicitação de Privacidade**.
- Use o botão **Selecionar** para abrir o diálogo popup do Tipo de Item de Menu.
- Na seção **Privacidade**, selecione o item **Confirmar Solicitação**.
- Se você não tiver um Menu Oculto, use seu menu principal e, na aba Tipo de Link, configure **Exibir no Menu** para **Não**.
- **Salvar & Fechar**.

## Itens do Menu do Administrador

Dê uma olhada nos outros itens de menu do Componente de Privacidade.

### Solicitações de Privacidade do Administrador

Esta tela é o local central para processar e gerenciar solicitações de
informações de usuários. Por favor, veja o artigo relacionado sobre Fluxo de Trabalho de Privacidade para orientações sobre como processar as solicitações.

![solicitações de informações de privacidade](../../../en/images/privacy/privacy-information-requests.png)

### Capacidades de Extensões

Esta tela coleta e exibe informações sobre as capacidades relacionadas
à privacidade informadas por extensões individuais. Ela é destinada a
auxiliar na preparação de documentação, como um artigo de política de privacidade ou um artigo de termos de serviço.

![capacidades de informações de privacidade](../../../en/images/privacy/privacy-extension-capabilities.png)

O conteúdo da página vem de cadeias de idioma no núcleo, no componente de privacidade e em plugins que implementam o evento onPrivacyCollectAdminCapabilities. Isso inclui:

- Autenticação
- Captcha
- Instalador
- Privacidade
- Sistema
- Usuário

As informações serão exibidas no idioma selecionado para o login do Administrador.

### Consentimentos

Esta tela exibe uma lista de consentimentos, do mais recente ao mais antigo. Ela será
exibida no idioma utilizado no formulário de consentimento, normalmente durante
o registro. Você pode pesquisar pelo nome de um usuário específico. Note que o consentimento para concordar com os Termos e Condições do site não é registrado aqui. Isso é registrado apenas no Log de Ações do Usuário.

![consentimentos de privacidade](../../../en/images/privacy/privacy-consents.png)

*Traduzido por openai.com*

