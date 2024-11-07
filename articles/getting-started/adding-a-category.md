<!-- Filename: J4.x:Getting_Started:_Adding_a_Category / Display title: Adicionando uma Categoria -->

## Introdução

Proprietários de sites com mais de alguns artigos devem pensar sobre a melhor forma de apresentar o conteúdo para facilitar a navegação. Por exemplo, se você tem um zoológico, um museu, uma coleção de minerais ou apenas um grande jardim, você pode ter cerca de 1000 espécimes para descrever. Um artigo para cada espécime, com fotografias, precisa de alguma estrutura organizacional. Se os artigos fossem arquivos, você provavelmente os colocaria em uma hierarquia de arquivos. Em um CMS, os artigos não são arquivos, mas as categorias oferecem uma estrutura semelhante a uma árvore. Exemplo:

| Categoria   | Subcategorias                         |
|-------------|---------------------------------------|
| Mamíferos   | Primatas, Macacos, Ungulados, Cães, Gatos |
| Répteis     | Cobras, Lagartos, Crocodilos, Tartarugas |
| Anfíbios    | Rãs, Sapos                           |
| Aves        | Rapinantes, Patos, Gaivotas, Pintassilgos, Chapins |
| Artrópodes  | Aranhas, Borboletas, Abelhas, Gafanhotos |
| Peixes      | Tubarões, Salmões, Bacalhaus, Arenques, Cavalas |

Subcategorias podem ter mais subcategorias também. A profundidade máxima gerenciável parece ser em torno de sete. Para a tabela acima, um museu pode adicionar mais categorias principais:

```text
natureza -> vida -> animais -> mamíferos...
natureza -> vida -> plantas -> árvores...
natureza -> minerais...
história -> egito...
ciência -> astronomia...
ciência -> química...
```

Imagine quantos espécimes um museu nacional ou de uma pequena cidade possui!

## Tipos de Itens de Menu

Existem vários tipos de itens de menu projetados para trabalhar com Categorias:

- **Blog de Categoria** Este é um layout de página que possui uma ou duas
  amostras de artigos destacadas, muitas vezes na largura total da página, em seguida,
  várias outras amostras de artigos em duas ou três colunas, e finalmente um 
  mecanismo de paginação para vincular a mais artigos na mesma categoria. 
  A amostra é o conteúdo antes de uma quebra de página, geralmente os 
  primeiros um ou dois parágrafos. A página *Inicial* de um site é 
  frequentemente um blog de categoria que inclui *Todas as Categorias*. Um 
  layout de *Artigos em Destaque* é semelhante a um blog de categoria e também 
  é frequentemente usado como uma página Inicial.
- **Lista de Categoria** Este é um layout de lista que exibe uma lista de 
  artigos em uma categoria. Pode ser exibido com um filtro de Pesquisa para 
  permitir a pesquisa de artigos por Título, Autor, Cliques, Tags ou Mês de publicação.
- **Listar Todas as Categorias em uma Árvore de Categorias de Artigos** Este layout lista uma 
  árvore de categorias a partir de um pai escolhido. Cada ramificação é recolhível e 
  é mais útil para grandes e complexas estruturas de árvores de categorias.

Os itens de menu são abordados em um artigo posterior.

## Criar uma Categoria

O exemplo a seguir utiliza uma categoria Mamíferos inspirada pela lista acima para demonstrar como criar uma nova Categoria:

![Formulário de edição de Categoria](../../../en/images/getting-started/article-category-edit.png)

- Selecione o item **Conteúdo** no menu do Administrador para expandi-lo.
- Selecione o ícone **+** ao lado do item de menu *Categorias* para abrir o formulário de edição de Categoria.
- O formulário **Artigos: Nova Categoria** possui apenas um campo obrigatório: o *Título*, neste caso *Mamíferos*.
- O campo **Descrição** é opcional, mas é melhor preenchê-lo, pois é usado em algumas listas. Sugestão:<br>
  *Mamíferos são animais de sangue quente que dão à luz filhotes vivos.*
- O campo **Pai** especifica se esta é uma categoria primária (-Sem Pai-) ou uma subcategoria selecionada a partir da lista de categorias.
- **Salvar e Fechar** para retornar à página de lista **Artigos: Categorias**.

Esta categoria está agora disponível para uso com artigos.

*Traduzido por openai.com*

