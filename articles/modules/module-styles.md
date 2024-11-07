<!-- Filename: jdocmanual?manual=user&heading=modules&filename=module-styles.md / Display title: Estilos de Módulo  -->

## Conceitos de Estilo

Um formulário de entrada de dados de módulo possui uma aba **Avançado**. Seus campos variam conforme o tipo de módulo, e você pode verificar isso por si mesmo, selecionando um módulo de Menu e comparando-o com um módulo de Login ou módulo de Breadcrumbs. Você verá os seguintes três campos de formulário relacionados ao estilo:

* **Classe do Módulo** é um campo de texto que permite adicionar sua própria classe CSS à tag de contêiner do módulo, geralmente um `<div>`.
* **Classe do Cabeçalho** é um campo de texto que permite adicionar sua própria classe CSS à Tag de Cabeçalho, por padrão uma tag `<h3>`.
* **Estilo do Módulo** é uma lista que permite selecionar um entre vários estilos padrão. A lista contém nenhum, html5, outline, table, card e noCard. O padrão é o card dos estilos do template Cassiopeia.

Você pode experimentar as opções de *Estilo do Módulo* editando um módulo e alterando o valor para ver o que isto faz na exibição do site.

* **html5** resulta em `<div class="moduletable ">`
* **none** remove completamente o `<div>` externo e também a tag `<h3>` do módulo.
* **outline** resulta em `<div class="mod_preview_info">`, com informações de posição e estilo substituindo a tag `<h3>` do módulo.
* **table** resulta em um layout de tabela começando por `<table class="moduletable ">` com a antiga tag h3 agora sendo uma tag `<th>`.
* **card** resulta em `<div class="sidebar-right card ">`, o padrão.
* **noCard** resulta em `<div class="sidebar-right no-card ">`

## A Classe de Módulo

Nesta etapa, você precisa saber um pouco sobre Folhas de Estilo em Cascata ou CSS. Se você inserir uma única palavra no campo Classe de Módulo, digamos **verde**, já que as classes CSS são por convenção todas em letras minúsculas, e com o Estilo do Módulo definido como **herdado**, a saída conterá `<div class="sidebar-right card green">`.

Não há mudança visível na aparência do site porque a classe "verde" não está definida. Para defini-la, faça uma entrada no arquivo user.css do template.

No menu do Administrador:
* Selecione **System / Site Templates / Cassiopeia Templates and Files**.
* Selecione **New File** na *Barra de Ferramentas*.
* Selecione **css** na coluna à esquerda, o destino para o novo arquivo.
* Digite **user** no campo Nome do Arquivo.
* Selecione **css** na lista de Tipo de Arquivo.
* Selecione o botão **Create**.

Agora você pode abrir a pasta css para encontrar e abrir o arquivo user.css para edição. Insira estas declarações de estilo e observe a ortografia americana de *color*:
```
.sidebar-right.card.green {
    background-color: #ddffdd;
}
.sidebar-right.card.green .card-body {
    background-color: #eeffee;
}
```
O estilo poderia ter usado apenas `.green`, mas isso poderia ter afetado outras etiquetas com esse estilo em outras páginas.

## A Classe Cabeçalho

Volte para o formulário de edição do módulo e adicione **blue** no campo da Classe Cabeçalho. O módulo não apresenta mudança visível no site, mas o cabeçalho agora aparece como `<h3 class="card-header blue">`. Retorne para editar o arquivo user.css para adicionar uma entrada para o estilo do cabeçalho:
```
.card-header.blue {
    color: navy;
}
```
O cabeçalho do módulo agora está em azul escuro. Existem várias maneiras de especificar cores em CSS. As mais comuns são hexadecimal e nomes padrão de cores. Leia tudo sobre isso em outro lugar!

## Desafio de CSS

* Altere a cor da borda do módulo para azul-marinho!
* Altere também a borda inferior do cabeçalho.
* Aplique esse estilo a vários módulos em vez de um por vez.

![Exemplo de Módulo de Artigos Arquivados](../../../en/images/modules/modules-archived-articles.png)

*Traduzido por openai.com*

