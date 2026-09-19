<!--
{
    "source": "https://jdocmanual.org/jdocmanual?article=user/templates/pagination-wrap",
    "title": "Quebra de linha da pagina\u00e7\u00e3o",
    "description": "Aprenda um m\u00e9todo simples para quebrar a linha da lista de pagina\u00e7\u00e3o em telas estreitas. ",
    "author": ""
}
-->

No Joomla, as listas de artigos, usuários e outros itens podem ser muito longas, por isso são exibidas em lotes, 20 por padrão. 

## A barra de paginação normal

Para navegar pelos lotes, há uma barra de paginação abaixo da lista de itens que permite ao usuário selecionar o próximo lote de itens, como nesta ilustração:

![a barra de paginação normal da lista](../../../en/images/templates/pagination-wrap/01-pagination-wide-screen.png)

## Paginação em telas estreitas

A barra de paginação funciona bem em telas largas. No entanto, em telas estreitas, a barra de paginação pode ser mais larga que a tela. Isso faz com que seja necessário rolar para a direita para encontrar outros itens na página, como os ícones de menu.

![a barra de paginação em uma tela estreita](../../../en/images/templates/pagination-wrap/02-pagination-narrow-screen.png)

Na ilustração acima, todos os itens na área cinza à direita estão *fora da tela* inicialmente e provavelmente passarão despercebidos. O usuário precisa rolar para a direita para vê-los. Nesse caso, os itens fora da tela são o ícone da barra de ferramentas no canto superior direito e o ícone de menu no canto inferior direito.

## Corrija com uma substituição de template

Esta correção adiciona uma classe *flex-wrap* ao código que gera a barra de paginação.

- No backend, acesse Sistema > Templates de administrador > Detalhes e arquivos do Atum
- Opcionalmente, selecione html > layouts apenas para ver o que há lá
- Selecione a aba **Criar substituições**
- Na caixa Layouts, selecione **joomla** e depois **pagination**
- Na aba Editor, selecione html > layouts > joomla > pagination > **links.php**
- Encontre a linha 70 que contém `<ul class="pagination ms-auto me-0">`
- Adicione `flex-wrap` à lista de classes: `<ul class="pagination ms-auto me-0 flex-wrap">`
- **Salvar e fechar**
- Opcional: você pode excluir /html/layouts/joomla/pagination/link.php e /html/layouts/joomla/pagination/links.php

Veja o resultado em telas largas e estreitas. A tela estreita agora mostra o ícone da barra de ferramentas e o ícone de menu na largura normal da tela:

![a barra de paginação modificada em uma tela estreita](../../../en/images/templates/pagination-wrap/02-modified-pagination-narrow-screen.png)

Para o template do site, siga estas instruções, mas crie uma substituição no template Cassiopeia.

*Traduzido por openai.com*