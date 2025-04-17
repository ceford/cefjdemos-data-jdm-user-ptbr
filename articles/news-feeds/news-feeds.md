<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-feeds.md / Display title: Feeds de Notícias  -->

## Introdução aos Feeds de Notícias

Era uma vez, era prática comum para um site exibir itens de notícias de sites remotos em uma página ou painel. Os navegadores até tinham leitores de notícias integrados para fazer exatamente isso. Os tempos mudaram, e os principais navegadores não oferecem mais essa opção. E há novos métodos para compartilhar conteúdo de sites, especialmente com as redes sociais.

O método para compartilhar notícias é a *Really Simple Syndication*, geralmente abreviada para **RSS**, e isso ainda tem um lugar na promoção de sites. A captura de tela a seguir mostra o *NetNewsWire*, um leitor de RSS gratuito e de código aberto para Mac. Outros leitores de RSS estão disponíveis para outras plataformas. A ilustração mostra o feed RSS de **Anúncios do Joomla!** selecionado. Dez anúncios são listados com título e breve descrição. O anúncio selecionado é exibido na íntegra na coluna da direita.

![Feed RSS dos Anúncios do Joomla](../../../en/images/news-feeds/news-netnewswire-display.png)

Imagine o que um ou mais feeds RSS podem fazer pelo seu site!  

## Configurando um Feed de Notícias

Seu site já possui Feeds de Notícias configurados automaticamente. Um site Joomla 5 recém-instalado tem essas duas linhas perto do topo do código-fonte da página inicial:

```
<link href="/j51/index.php?format=feed&amp;type=rss" rel="alternate" type="application/rss+xml" title="Home">
<link href="/j51/index.php?format=feed&amp;type=atom" rel="alternate" type="application/atom+xml" title="Home">
```
Essas linhas permitem que sistemas automatizados usem Feeds RSS ou Atom. Atom é uma especificação de sindicação de notícias mais recente e ligeiramente diferente. As linhas estarão presentes em todas as páginas **Destaque** e páginas de **Blog de Categoria**, mas não na maioria dos outros tipos de página. Você pode desativar a inclusão desses feeds RSS se desejar.

## Alternar Link do Feed RSS

A configuração global do Link do Feed RSS é encontrada na aba **Integração** da página Opções dos Artigos. Configure para *Mostrar* ou *Ocultar* conforme desejar. O padrão é **Mostrar**.

A configuração global pode ser alterada em um item de menu do blog de Categoria. Novamente, selecione a aba *Integração* e configure o *Link do Feed RSS* para *Mostrar* ou *Ocultar*.

O Feed RSS não pode ser ocultado em uma página inicial de Artigos em Destaque (bug?)!

## O Módulo de Feeds de Sindicação

Há um módulo principal que você pode colocar em páginas de Blog Destacado ou Categoria para fornecer um link de Sindicação. Preencha os campos na guia do Módulo. A maioria tem valores padrão adequados. Se o campo Rótulo for deixado em branco, o rótulo padrão em inglês será *Feed Entries*. Na guia *Atribuição de Menu*, selecione **Em todas as páginas**. O módulo só aparecerá em páginas de Blog Destacado e de Categoria.

![Entrada de dados de feeds de sindicação](../../../en/images/news-feeds/news-syndication-feeds-form.png)

Lembre-se de atribuir o módulo a uma *Posição* e marcá-lo como *Publicado*.

Na visualização da página do site, o módulo exibe um link. Não é para ser clicado, a menos que você tenha um Leitor de Notícias local configurado. O link precisa ser copiado para uso em um Leitor de Notícias em outro site ou aplicativo de Leitor de Notícias.

![Exibição de feeds de sindicação](../../../en/images/news-feeds/news-syndication-feeds-display.png)

Observe que o link é para os itens dessa página. Portanto, se o seu site tiver várias páginas de blog de categoria, você terá vários feeds RSS diferentes.

*Traduzido por openai.com*

