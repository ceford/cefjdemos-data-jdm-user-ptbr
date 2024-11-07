<!-- Filename: J4.x:Switching_Templates / Display title: Alternando Modelos -->

## Modelos de Site e Administrador

O Joomla 4 vem com um único modelo de Site, Cassiopeia, e um único modelo de Administrador, Atum. Você pode obter modelos adicionais de fornecedores de modelos de terceiros, tanto gratuitos quanto pagos, e pode criar seus próprios modelos, mais facilmente como modelos filho.

É improvável que você queira usar um modelo de Administrador alternativo, então este artigo cobre apenas modelos de Site alternativos. Para ilustração, um modelo filho foi criado com um tema verde, conforme descrito no artigo sobre Modelos Filhos. Além disso, o site usado para ilustração tem os Dados de Amostra para Teste instalados.

## Estilo de Template Padrão

Um dos seus templates deve ser marcado como padrão. Ele é usado para todas as
páginas, exceto para aquelas páginas individuais que especificam um template alternativo.
Para definir o template padrão:

- Selecione **Sistema → Painel de Templates → Estilos de Templates do Site** 
  no menu do Administrador.
- Selecione um dos botões na coluna Padrão.

![página de lista de estilos de templates do site](../../../en/images/templates/switch-templates-styles-list.png)

Dê uma olhada no seu site para verificar se todas as páginas estão utilizando o
template padrão.

## Usando um Estilo Alternativo

O Joomla permite que você selecione um estilo para uma página específica a partir de sua atribuição de menu. A seleção pode ser feita a partir do formulário de Estilo do Template ou do formulário de Edição de Menu. Ambos os métodos produzem o mesmo resultado. O primeiro método é mais conveniente para seleção de um grupo de itens de menu pertencentes ao mesmo menu.

### Método de Atribuição de Menu do Template

Da lista de Templates: Estilos:

- Selecione um estilo que **não** esteja definido como padrão. A estrela amarela indica o estilo padrão.
- Selecione a aba Atribuição de Menu.
- Selecione itens de menu individuais ou alterne todos os itens em um menu.
- Salve

![aba de atribuição de menu na página de edição de estilo de templates](../../../en/images/templates/switch-templates-styles-edit-style-menu-assignment.png)

Neste exemplo, todos os itens de menu no menu `Main Menu Testing` foram selecionados. Retorne ao seu site e selecione qualquer um dos itens de menu que devem usar o template selecionado.

### Método de Detalhes do Menu

Este método é usado para definir o template para itens de menu individuais.

- Selecione **Menus → \[Nome do Menu\]** do menu do Administrador.
- Selecione um link de item de menu na coluna Título para abrir o formulário de edição.
- No campo **Estilo do Template**, selecione o estilo de template desejado.
- Salve

![formulário de edição de item de menus de templates mostrando seleção de estilo](../../../en/images/templates/switch-templates-styles-edit-menu-style.png)

Retorne ao seu site e selecione o item de menu alterado para verificar se ele é exibido com o estilo de template selecionado.

*Traduzido por openai.com*

