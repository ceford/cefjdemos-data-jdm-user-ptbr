<!-- Filename: J4.x:Home_Page_in_Different_Style / Display title: Página Inicial em Estilo Diferente   -->

## Página Inicial do Site

Uma página inicial do site pode ser selecionada a partir de qualquer tipo de item de menu escolhendo um ícone cinza na coluna Home de qualquer lista de itens de menu. Experimente fazer uma alteração! Veja a alteração no seu site em uma aba ou janela de navegador separada. Você pode facilmente voltar à configuração anterior. Se você quiser uma página inicial distinta, pode optar por um tipo de item de menu de Artigo Único, um tipo de item de menu de Blog de Categoria, um tipo de item de menu de Artigos em Destaque, ou outra coisa.

Suponha que você gostaria de dar à sua página inicial uma aparência distintiva, um pouco diferente de todas as outras páginas do seu site. Existem muitos métodos diferentes disponíveis para personalizar a aparência de uma página inicial:

- Através de módulos atribuídos apenas à página inicial.
- Através de estilos personalizados.
- Através de uma substituição de template ou layout.
- Através de um template separado ou um template filho usado apenas para o item de menu da página inicial.
- Mais...?

## Exemplo: Dados de Amostra Cassiopeia

Os dados de amostra Cassiopeia criam uma página inicial usando um tipo de item de menu **Artigos em Destaque**. Ela está organizada com a aparência mostrada na captura de tela abaixo (algumas pequenas alterações foram feitas em artigos individuais para melhorar a captura de tela aqui).

![página inicial usando cassiopeia e dados de amostra](../../../en/images/templates/templates-home-page-style-cassiopeia-sample-data.png)

É assim que o layout é alcançado:

### Módulo de Imagem

A imagem grande abaixo da barra de menu está em um módulo personalizado chamado Imagem, atribuído à posição banner no modelo Cassiopeia.

![módulo personalizado usado no estilo de dados de amostra](../../../en/images/templates/templates-home-page-style-custom-module-image.png)

Na aba Atribuição de Menu, o módulo é atribuído apenas à página inicial:

![aba de atribuição de menu do módulo personalizado](../../../en/images/templates/templates-home-page-style-custom-module-menu-assignment.png)

A imagem de fundo é selecionada na aba Opções do formulário de edição de Módulos: Personalizado.

Na aba Avançado / campo Layout, o item `banner` é selecionado. O layout banner é um layout de modelo:

### Layout de Modelo

O layout padrão do módulo em `siteroot/modules/mod_custom/tmpl/default.php` não exibe o módulo conforme desejado. Existe um layout alternativo em `siteroot/templates/cassiopeia/html/mod_custom/banner.php`. Como `banner.php` não está presente no código do módulo personalizado, ele funciona como um layout que você pode selecionar em vez de uma substituição que é sempre usada. No módulo de Imagem, você pode selecionar o layout padrão, salvar e recarregar o site para ver a diferença. Alterne de volta para o layout de banner e salve novamente para restaurar o comportamento normal.

Há artigos separados sobre Substituições e Layouts.

### Módulo Newsflash

Abaixo da grande imagem, há três pequenas caixas, cada uma com uma imagem e texto abaixo. Elas são criadas usando um módulo Artigos - Newsflash na posição top-a do modelo. O módulo é configurado para exibir 3 itens. A atribuição do menu é apenas para a página inicial. A aba Avançado tem o Layout definido como horizontal e o Estilo do Módulo definido como noCard.

![módulo newsflash](../../../en/images/templates/templates-home-page-style-newsflash-module-image.png)

Isso conclui a explicação de como a página inicial dos dados de amostra Cassiopeia foi criada.  

## Mais Opções

Você pode querer fazer mais. Um esquema de cores diferente para a página inicial, uma marca d'água ou um layout personalizado. Aqui estão algumas ideias:

### Exibição de Página

Nos menus: No formulário de edição do item para o menu Inicial, selecione a aba Exibição de Página. O campo Classe da Página geralmente está vazio. Qualquer coisa inserida aqui se torna uma classe extra no elemento `<body>` da página. Por exemplo, inserindo `fancyhome`, resulta no seguinte na saída da página inicial para essa página específica:
```html
<body class="site com_content wrapper-static view-featured no-layout no-task itemid-101 fancyhome has-sidebar-right">
```
Você pode então criar um arquivo user.css via **Sistema** → **Modelos de Site** → **Detalhes e Arquivos do Cassiopeia**. Selecione o botão `Novo Arquivo` e crie user.css na pasta css. Em seguida, insira estilos no formulário de edição do user.css. Exemplo:
```css
    .fancyhome {
      background-color: #f8fff8;
    }
```
Isso dará à página inicial um fundo verde claro. Use \#f8f8ff para um fundo azul claro ou \#ffffee para amarelo claro. Você pode fazer todo tipo de coisas com seu estilo fancyhome, mas precisa de um bom conhecimento de css.

### Templates Alternativos para a Página Inicial

Você pode instalar templates alternativos para o site, obtidos de fornecedores de templates de terceiros. E você pode criar templates filhos que se comportam de maneira semelhante. Em ambos os casos, você pode escolher qual template será o padrão para todas as páginas e qual será usado apenas para a página inicial.

- Selecione **Sistema → Estilos de Template de Site** no menu do Administrador.
- Selecione o template que deseja usar para a página inicial. Deve ser um dos que não estão selecionados como template padrão.
- Na aba Atribuição de Menu, selecione apenas o item do menu Inicial. Qualquer coisa não selecionada aqui ainda usará seu template padrão.
- Você pode selecionar algumas opções na aba Avançado, mas elas variam com cada template e não são abordadas aqui.

Existem outros artigos sobre personalização do Cassiopeia.

*Traduzido por openai.com*

