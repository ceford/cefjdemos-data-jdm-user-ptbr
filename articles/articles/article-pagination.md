<!-- Filename: J4.x:Article_Pagination / Display title: Artigo: Edição - Paginação  -->

## Artigos Longos

O único limite para o comprimento de um artigo no Joomla é o tamanho do campo do banco de dados utilizado para conter o texto do artigo. Esse tamanho é muito grande! Artigos longos podem conter muitas imagens e levar tempo para serem processados, o que pode ser inconveniente para o leitor e o site. Portanto, há um mecanismo simples para dividir artigos longos em páginas separadas com um índice.

## Inserir uma Quebra de Página

Para adicionar quebras de página, primeiro abra um artigo no editor de texto, TinyMCE
é o padrão, e proceda da seguinte forma:

- Posicione o cursor no local onde deseja que ocorra a quebra de página.
- Na lista suspensa **Conteúdo do CMS**, selecione o item *Quebra de Página*.
- Na caixa de diálogo Quebra de Página, insira:
  - *Título da Página* - isto será anexado ao título da página existente.
    Exemplo: Página 2
  - *Alias do Índice* - isto será usado como texto no Índice.
    Exemplo: Capítulo 2
- Selecione o botão **Inserir Quebra de Página**.

![Formulário de diálogo de quebra de página](../../../en/images/articles/articles-edit-pagination.png)

- Repita para cada quebra de página que você deseja criar.
- Salve o artigo e confira a Prévia ou a visualização no Site.

![Visualização de paginação do artigo no site](../../../en/images/articles/articles-site-pagination.png)

## Editar ou Mover uma Quebra de Página

Você pode selecionar uma quebra de página e excluí-la. No entanto, você não pode cortá-la e colá-la, e não pode abrir uma quebra de página existente no formulário de Quebra de Página. Então, para mover ou alterar uma quebra de página, use o editor de Código-Fonte da seguinte forma:

- Selecione o item **Ferramentas -> Código-fonte+** do editor de texto.
- O editor de código-fonte mostra o HTML com realce de sintaxe.
- Role para baixo até a quebra de página que deseja editar ou mover.
- Para mover uma quebra de página:
  - Selecione e Corte a linha contendo a quebra de página.
  - Coloque o cursor na nova posição e Cole a linha cortada.
- Para editar:
  - Altere o texto do título e/ou o texto alternativo conforme necessário.
- Selecione **Salvar**.
- Salve o artigo e verifique a Prévia ou a visualização do Site.

O editor de Código-fonte está localizado em um diálogo popup:

![Editor de código-fonte](../../../en/images/articles/articles-edit-pagination-source-code.png)

*Traduzido por openai.com*

