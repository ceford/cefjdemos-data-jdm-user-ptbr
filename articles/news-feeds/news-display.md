<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-display.md / Display title: Exibição de Notícias -->

## O Módulo de Exibição de Feed

Existe um módulo central de *Exibição de Feed* disponível para mostrar notícias de outros sites. A captura de tela a seguir mostra o formulário de entrada de dados com a URL do feed de notícias de Anúncios do Joomla. Note que a Contagem de Palavras está definida para 100. Caso contrário, o comprimento de um anúncio pode ser excessivo para um módulo de barra lateral.

![Entrada de dados do módulo de exibição de feed](../../../en/images/news-feeds/news-joomla-news-form.png "Entrada de dados do módulo de exibição de feed")

O resultado pode não ser esteticamente agradável, mas pode ser melhorado com alguns estilos personalizados em user.css:

![Entrada de dados do módulo de exibição de feed](../../../en/images/news-feeds/news-joomla-news-display.png "Entrada de dados do módulo de exibição de feed")

## Páginas de Exibição de Feed

Como alternativa à exibição de notícias em um módulo, você pode criar um item de menu para exibir um feed de notícias em uma página web. No menu do Administrador:

* Selecione **Componentes / NewsFeeds / Feeds**. Você pode primeiro criar uma Categoria para as notícias.
* Selecione o botão **Novo** na *Barra de Ferramentas*.
* Preencha o formulário **Feeds de Notícias: Editar**:
    - O **Link** é o link RSS copiado de uma fonte remota.
    - A **Descrição** é opcional.
    - A aba **Opções** tem itens para controlar a *Exibição* do feed.
* **Salvar & Fechar**

![Entrada de dados do componente NewsFeed](../../../en/images/news-feeds/news-feed-data-entry.png "Entrada de dados do componente NewsFeed")

Crie um item de menu partindo do menu do Administrador:

* Selecione **Menus / Menu Principal** ou qualquer outro menu para este item.
* Selecione **Novo** na Barra de Ferramentas *Menus: Itens*.
* No campo **Tipo de Item de Menu**, use o botão **Selecionar** para encontrar e selecionar *News Feeds / Feed de Notícias Único*.
* Preencha o restante do formulário conforme apropriado.
* **Salvar & Fechar**

![Entrada de dados do item de menu NewsFeed](../../../en/images/news-feeds/news-feed-data-entry.png "Entrada de dados do item de menu NewsFeed")

Teste: vá ao menu do Site e selecione o item de menu do Feed.

![Exibição do NewsFeed](../../../en/images/news-feeds/news-feed-display.png "Exibição do NewsFeed")

Cada item no feed é um `<li>` dentro de uma tag `<ul>`, então, por padrão, aparece marcado por um marcador. Isso não é tão evidente se os itens forem longos. Você pode aplicar seus próprios estilos em *user.css*. O seguinte colocará cada item em uma caixa distinta:

```css
ul.com-newsfeeds-newsfeed__items {
  list-style-type: none;
  padding-left: 0;
}

ul.com-newsfeeds-newsfeed__items > li {
  padding: 1rem;
  margin-bottom: 1rem;
  border: 2px solid navy;
}
```
Que aparece assim:

![Exibição personalizada do NewsFeed](../../../en/images/news-feeds/news-feed-custom-display.png "Exibição personalizada do NewsFeed")

## Listar Feeds de Notícias em uma Categoria

A página *Joomla! Feeds de Notícias RSS* lista oito feeds de notícias separados. Você pode criar um feed para alguns ou todos eles e atribuí-los a uma Categoria, digamos *Notícias Joomla*. Em seguida, você pode criar um item de menu com o *Tipo de Item de Menu* definido como *Listar Feeds de Notícias em uma Categoria* e a Categoria definida como *Notícias Joomla*.

![Formulário de menu de feed de notícias por categoria](../../../en/images/news-feeds/news-feed-menu-category-form.png "Formulário de menu de feed de notícias por categoria")

Experimente para ver o resultado!

*Traduzido por openai.com*

