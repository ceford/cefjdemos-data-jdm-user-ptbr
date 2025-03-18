<!-- Filename: J5.x:Managing_Mail_Template_Layout / Display title: Modelos de E-mail -->

## Introdução

Os Modelos de E-mail são usados para enviar mensagens de e-mail do sistema em **texto simples** ou **HTML** ou ambos, selecionados no formulário *Modelos de E-mail: Opções*. Se apenas um método for selecionado, a alternativa não estará presente no formulário de edição de mensagens.

A captura de tela a seguir mostra uma seleção dos 26 Modelos de Email padrão disponíveis. A lista está disponível selecionando **Sistema -> Modelos de Email** no menu do Administrador.

![mail templates list](../../../en/images/templates/mail-templates-list.png)

As mensagens de e-mail podem ser personalizadas para alterar o layout, a aparência e o texto para atender às necessidades do seu site. Por exemplo, você pode querer usar um logotipo do site e esquema de cores nos e-mails enviados aos clientes. A personalização dos e-mails enviados aos administradores é menos importante.

Existem dois métodos de personalização: através do *Mail Template: Options* para todos os modelos de e-mail e através do *Per Template Mail Settings*.

## Modelo de E-mail: Opções

Selecione o botão **Opções** na barra de ferramentas da lista de *Modelos de E-mail* para acessar as configurações gerais do modelo de e-mail. Selecione o botão *Alternar Ajuda em Linha* para verificar se algum dos campos do formulário tem ajuda extra.

![mail templates options](../../../en/images/templates/mail-templates-options.png)

### Formato de E-mail

Esteja ciente de que um destinatário pode configurar um cliente de e-mail para usar HTML simples ou Texto Simples para evitar o download de imagens. Portanto, pode ser melhor definir o *Formato do E-mail* para *Texto Simples* ou *Ambos*.

### Configurações de E-mail por Modelo

Se isso estiver definido como **Sim**, os formulários de edição de modelos de e-mail individuais terão uma aba extra de *Opções* que permite alterar as configurações de e-mail para aquele modelo e, opcionalmente, permitir que você envie uma cópia (BCC) para um endereço de e-mail específico, desde que o campo **Enviar Cópia** aqui também esteja definido como **Habilitado**.

## Formulário de Edição de Template

Na lista de Modelos de E-mail, você pode selecionar qualquer modelo para editar. O link Título leva ao formulário de edição para o modelo padrão em inglês. Cada bandeira é um link para o mesmo modelo naquele idioma.

### A guia Correio

![edit mail template form](../../../en/images/templates/mail-template-edit.png)

O conteúdo das áreas de Assunto e Corpo são armazenados inicialmente em strings de linguagem. Isso facilita na hora de *Redefinir Para o Assunto Padrão* ou o *Corpo*. No entanto, uma vez que um modelo de e-mail específico tenha sido editado, seus campos de Assunto e Corpo são armazenados na tabela `#__mail_templates`.

Os itens entre chaves são marcadores de posição que são substituídos por valores reais quando o e-mail é enviado. No exemplo acima, `{SITENAME}` seria qualquer nome que você escolhesse para o seu site. `{Method}` seria o método de transporte de e-mail selecionado: `PHP Mail`, `Sendmail` ou `SMTP`.

As tags de espaço reservado disponíveis variam de e-mail para e-mail. Você pode adicionar suas próprias tags de espaço reservado personalizadas, mas isso requer um plugin personalizado, descrito em um [artigo da Revista](https://magazine.joomla.org/all-issues/february-2025/joomla-5-email-templates-how-to-add-variables-via-plugin) de fevereiro de 2025.

### A guia Opções

Esta guia está presente apenas se as *Configurações de Email por Modelo* estiverem definidas como *Sim* em *Modelos de Email: Opções*. A ilustração abaixo mostra uma captura de tela com as *Configurações de Email* definidas como *Não*. Se definido como *Sim*, mais campos de formulário aparecem, substituindo as opções de Email definidas na Configuração Global, guia Servidor.

![edit mail template form](../../../en/images/templates/mail-template-edit-options.png)

Se você deseja enviar uma cópia oculta de um email saindo para um endereço de email específico, você pode inseri-lo no campo *Enviar Cópia Para o Email*.

## Substituições de Modelos de E-mail

Para criar uma substituição de modelo de e-mail dentro de um modelo personalizado:

1. Vá para Sistema -> Modelos do Site -> Abra seu modelo (por exemplo, Cassiopeia).
2. Na aba Criar Substituições, selecione joomla -> mail.
3. O Joomla irá copiar o arquivo `mailtemplate.php` para o diretório `/html/layouts/joomla/mail/` do seu modelo, onde você pode modificá-lo conforme necessário.

Depois que a substituição for criada, você pode ajustar o layout e os estilos dos seus e-mails sem afetar o modelo base.

## Lista de Modelos de E-mail

| Título | Extensão | Descrição |
|-------|-----------|-------------|
| Log de Ações do Usuário: E-mail de Notificação | Log de Ações do Usuário | E-mail enviado aos administradores sobre novas entradas no Log de Ações do Usuário. |
| Configuração Global: E-mail de Teste | Configuração | Enviado quando você clica no botão "Enviar E-mail de Teste" na Configuração Global. É enviado para o endereço de e-mail de envio que está configurado nas configurações de e-mail. |
| Contatos: E-mail do Formulário de Contato | Contatos | O e-mail do "Formulário de Contato". |
| Contatos: Cópia do E-mail do Formulário de Contato | Contatos | Enviado ao remetente de um e-mail com o formulário de contato se a opção "Enviar Cópia ao Remetente" estiver habilitada e selecionada. |
| Mensagens: Nova mensagem | Mensagens | E-mail contendo uma mensagem criada no componente de mensagens. |
| Privacidade: Solicitação de Exportação de Dados (Admin) | Privacidade | E-mail para informar o usuário que uma solicitação para exportar os dados deste site foi criada pelo administrador. |
| Privacidade: Solicitação de Remoção de Dados (Admin) | Privacidade | E-mail para informar o usuário que uma solicitação para remover os dados deste site foi criada pelo administrador. |
| Privacidade: Solicitação de Exportação de Dados | Privacidade | E-mail para verificar se os dados de um usuário devem ser exportados do site. |
| Privacidade: Solicitação de Remoção de Dados | Privacidade | E-mail para verificar se os dados de um usuário devem ser removidos do site. |
| Privacidade: Exportação de Dados do Usuário | Privacidade | E-mail com exportação de dados do usuário. |
| Usuários: E-mail em Massa para Usuários | Usuários | O e-mail de "E-mail em Massa para Usuários". |
| Usuários: Redefinição de Senha | Usuários | Enviado a um usuário pelo link "Esqueceu sua senha?" por exemplo, em um formulário de login. |
| Usuários: Notificação de nova conta para admin | Usuários | Notificação ao administrador de que uma nova conta ativada foi criada. |
| Usuários: Solicitação ao admin para verificar nova conta | Usuários | Notificação aos administradores para verificar uma nova conta verificada. |
| Usuários: Conta ativada pelo administrador | Usuários | Notificação enviada ao usuário de que a nova conta foi ativada por um administrador. |
| Usuários: Nova conta com ativação pelo administrador | Usuários | Notificação sobre nova conta ao usuário, que agora terá que ser ativada por um administrador. |
| Usuários: Nova conta com ativação pelo administrador (com senha) | Usuários | Notificação sobre nova conta ao usuário, que agora terá que ser ativada por um administrador. A senha em texto claro está incluída no e-mail. |
| Usuários: Nova conta sem ativação | Usuários | Notificação sobre nova conta ao usuário. A conta já está ativada. |
| Usuários: Nova conta sem ativação (com senha) | Usuários | Notificação sobre nova conta ao usuário. A conta já está ativada. A senha em texto claro está incluída no e-mail. |
| Usuários: Nova conta com autoativação | Usuários | Notificação sobre nova conta ao usuário, que agora terá que autoativar. |
| Usuários: Nova conta com autoativação (com senha) | Usuários | Notificação sobre nova conta ao usuário, que agora terá que autoativar. A senha em texto claro está incluída no e-mail. |
| Usuários: Lembrete de Nome de Usuário | Usuários | Enviado a um usuário pelo link "Esqueceu seu nome de usuário?" por exemplo, em um formulário de login. |
| Código enviado por e-mail | Autenticação Multi-fator - Código de Autenticação por E-mail | Enviado aos usuários pela página de Autenticação Multi-fator ao usar a opção "Código de Autenticação por E-mail". |
| Tarefa - Consentimento de Privacidade: Renovar Consentimento | Tarefa - Consentimentos de Privacidade | Lembrete para renovar o consentimento de privacidade para este site. |
| Joomla: Notificação de Atualização | Tarefa - Notificação de Atualização do Joomla! | Enviado aos administradores do site quando o plugin de tarefa "Notificação de Atualização do Joomla!" detecta uma atualização. |
| Usuários: Novo Usuário | Usuário - Joomla! | Enviado a um novo usuário quando criado no backend. |

*Traduzido por openai.com*

