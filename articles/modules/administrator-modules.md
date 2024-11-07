<!-- Filename: J4.x:Administrator_Modules / Display title: Módulos do Administrador  -->

## Introdução

O template do Administrador Atum é fornecido com um conjunto completo de módulos de Administração instalados e configurados para uso diário. A ilustração a seguir mostra as posições do Painel Inicial para indicar onde os módulos estão localizados.

![posições do painel inicial do atum](../../../en/images/modules/atum-template-positions.png)

Na ilustração acima, os painéis são instâncias do módulo Ícone Rápido vinculadas a plugins quickicon.

### Notas sobre algumas posições de Módulos

- **Custom Top** está acima do banner e é útil se você deseja publicar um menu Personalizado ou um módulo Personalizado contendo uma mensagem importante. Por exemplo, para avisar os Administradores que o site será fechado em breve para manutenção do sistema.
- **Status** é para os ícones mostrados alinhados à direita no Banner.
- **Menu** está na barra lateral esquerda da tela do Atum.
- **Toolbar** está acima da área de Conteúdo Principal nas telas de lista e edição, mas não está presente nas telas do painel.
- **Top** está abaixo da Toolbar, mas acima de qualquer Mensagem do Sistema e do conteúdo do componente.
- **Bottom** está abaixo do conteúdo do componente.
- **Debug** está abaixo de tudo.

Posições do template Atum por nome

```xml
  <positions>
    <!-- usado diretamente no template -->
    <position>bottom</position>
    <position>cpanel</position>
    <position>customtop</position>
    <position>debug</position>
    <position>icon</position>
    <position>login</position>
    <position>menu</position>
    <position>sidebar</position>
    <position>status</position>
    <position>title</position>
    <position>toolbar</position>
    <position>top</position>
  </positions>
```

## Adicionar um Módulo Personalizado

Você pode querer adicionar um módulo personalizado para avisar os administradores sobre algum problema no sistema. Selecione **Conteúdo → Módulos do Administrador** no menu do administrador. A lista de módulos instalados é bastante longa:

![lista de módulos do administrador atum](../../../en/images/modules/atum-admin-modules-list.png)

Selecione o botão Novo e, em seguida, o módulo Personalizado. No formulário de edição de Módulos: Personalizado, insira um Título, uma Mensagem Personalizada e selecione uma Posição para o módulo. No exemplo abaixo, foi selecionada a posição Superior. Além disso, na guia Avançado, no campo Classe do Módulo, alguns estilos foram inseridos para centralizar o texto e adicionar algum espaçamento: **alert alert-warning text-center**. Salve para ver o resultado. Feche para ver o resultado na página da lista de Módulos.

![mensagem do sistema de edição de módulo personalizado atum](../../../en/images/modules/atum-admin-module-system-message.png)

Quando você terminar com a mensagem, basta selecionar o botão de Status na lista de módulos para Despublicar o módulo.

## Lista de Módulos de Administrador

- **Logs de Ações - Mais Recentes** Este módulo mostra uma lista das ações mais recentes.
- **Menu do Painel do Administrador** Este módulo exibe um sub-menu do administrador.
- **Menu do Administrador** Este módulo exibe um módulo de menu do administrador.
- **Artigos - Mais Recentes** Este módulo mostra uma lista dos artigos criados mais recentemente.
- **Personalizado** Este módulo permite que você crie seu próprio módulo usando um editor WYSIWYG.
- **Exibição de Feed** Este módulo permite a exibição de um feed sindicado.
- **Link do Frontend** Este módulo mostra um link para o frontend e é destinado a ser exibido na posição 'status'.
- **Informações da Versão do Joomla!** Este módulo exibe a versão do Joomla! e é destinado a ser exibido na posição 'status'.
- **Usuários Conectados** Este módulo mostra uma lista dos usuários conectados.
- **Formulário de Login** Este módulo exibe um formulário de login com nome de usuário e senha. Ele não deve ser despublicado.
- **Informações de Suporte de Login** Este módulo exibe alguns links úteis para sites de suporte do Joomla na tela de login.
- **Mensagens** Este módulo mostra a contagem de mensagens privadas e é destinado a ser exibido na posição 'status'. Só é exibido quando há mensagens para ler.
- **Status Multilíngue** Este módulo mostra o status dos parâmetros multilíngues e é destinado a ser exibido na posição 'status'.
- **Artigos Populares** Este módulo mostra uma lista dos artigos publicados mais populares que ainda estão vigentes. Alguns que são mostrados podem ter expirado, mesmo sendo os mais recentes.
- **Mensagens Pós-Instalação** Este módulo mostra um contador e um link para as últimas mensagens pós-instalação. Só é exibido quando há mensagens para ler.
- **Painel de Privacidade** O Módulo de Painel de Privacidade mostra informações sobre solicitações de privacidade.
- **Verificação do Status de Privacidade** O Módulo de Verificação do Status de Privacidade mostra informações sobre o status de privacidade dos seus sites.
- **Ícones Rápidos** Este módulo mostra Ícones Rápidos que são visíveis no Painel Principal (página inicial da área do administrador).
- **Dados de Exemplo** Este módulo permite que você instale dados de exemplo.
- **Estatísticas** O Módulo de Estatísticas mostra informações sobre sua instalação de servidor juntamente com estatísticas sobre os usuários do site e o número de artigos em seu banco de dados.
- **Título** Este módulo mostra o Título do Componente da Barra de Ferramentas.
- **Barra de Ferramentas** Este módulo mostra os ícones da barra de ferramentas usados para controlar ações em toda a área do Administrador.
- **Menu do Usuário** Este módulo mostra o Menu do Usuário e é destinado a ser exibido na posição 'status'.

*Traduzido por openai.com*

