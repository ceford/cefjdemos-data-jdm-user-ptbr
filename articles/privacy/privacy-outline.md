<!-- Filename: Help4.x:Components_Privacy_Outline / Display title: Esboço de Privacidade -->

## Conteúdo

O Joomla Privacy Tool Suite consiste nas seguintes partes:

- **Componente Administrador** Gerencia as solicitações de privacidade das informações do usuário.
- **Módulo - Painel de Privacidade** Adiciona um painel de privacidade no Painel Inicial.
- **Módulo - Solicitações de Privacidade** Adiciona um painel de solicitações de privacidade no Painel de Privacidade.
- **Módulo - Status de Privacidade** Adiciona um painel de status de privacidade no Painel de Privacidade.
- **Item de Menu - Criar Solicitação** Exibe um formulário para mostrar uma Solicitação de Informação. Para ser criado.
- **Plugin - Sistema - Consentimento de Privacidade** Adiciona campos de consentimento aos formulários de informações pessoais, como o de Registro. Para ser habilitado.
- **Plugin - Usuário - Termos e Condições** Solicita o consentimento do usuário para os termos e condições do site. Para ser habilitado.
- **Plugin - Conteúdo - Confirmar Consentimento** Adiciona uma caixa de seleção obrigatória a um formulário, por exemplo, o formulário de contato principal. Para ser habilitado.
- **Plugin - Privacidade - Diversos** Mais plugins, habilitados por padrão, sem parâmetros significativos para configurar.

Na instalação, o Privacy Tool Suite está pronto para uso pelo Administrador sem necessidade de habilitar plugins ou criar um item de menu.

## Fluxo de Trabalho

Esta é uma sequência típica de eventos:

- Um pedido de informação chega. Ele deve incluir um endereço de e-mail válido
  para um Titular dos dados. O Titular não precisa ser um usuário registrado.
  Por exemplo, o Titular pode ser um contato adicionado por um Administrador.
- Se a mensagem não for enviada pelo Titular através de um formulário de
  Informações Pessoais do site:
  - O Administrador vai para
    **Usuários → Privacidade → Pedidos → Novo** para criar um novo
    pedido de informação. Uma mensagem é enviada para o endereço de e-mail fornecido
    convidando o Titular a confirmar que este é um pedido genuíno.
- Se a mensagem for enviada através de um formulário de Informações Pessoais do site,
  o Titular recebe automaticamente uma mensagem de pedido de confirmação.
- O Titular seleciona o link na mensagem de e-mail para abrir o
  formulário de confirmação. Após o envio, o Titular vê uma mensagem de confirmação.
- O Administrador vê que Mensagens Privadas na Barra de Título tem
  mensagens pendentes. Também haverá uma mensagem de e-mail do sistema.
- O Administrador vai para **Usuários → Privacidade → Pedidos** e
  vê que o status do pedido mudou para **Confirmado**.
- Para um pedido de Exportação de dados, há botões adjacentes de Exportar e E-mail.
  - O Administrador seleciona o botão Exportar para dar uma olhada nos
    dados a serem exportados. Isso está em formato XML, mas é exibido de forma sensata no
    Firefox.
  - O Administrador seleciona o botão E-mail para enviar os dados exportados
    para o Titular.
- Para um pedido de Remoção de dados, há um botão Delete adjacente.
  - O Administrador seleciona o botão excluir para anonimizar os dados
    do usuário. O usuário não pode mais fazer login.
- Selecione o endereço de e-mail do Titular dos dados para abrir o formulário de Revisão
  de Pedido de Informação.
- Selecione o botão Completar na Barra de Ferramentas.
- A lista de Pedidos de Informação mostra o status como Completo e os
  botões de Ação desapareceram.

Observe que esta suíte não exibe um formulário de permissões de Cookies.

*Traduzido por openai.com*

