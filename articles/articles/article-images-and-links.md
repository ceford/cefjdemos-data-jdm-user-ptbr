<!-- Filename: Article_Images_and_Links / Display title: Artigo: Editar - Imagens e Links -->

## Introdução

Outros artigos descreveram como incorporar imagens e links no conteúdo de um artigo. Este artigo descreve o uso da aba *Imagens e Links* para adicionar dois tipos de imagem e até três links que serão utilizados em layouts padronizados. Em resumo:

- A *Imagem de Introdução* é usada em layouts de Blog de Categoria ou Lista como um teaser visual extra do tipo de conteúdo a ser esperado.
- A *Imagem do Artigo Completo* é colocada no topo do artigo completo como uma introdução visual ao conteúdo.
- Os links: Link A, Link B e Link C são colocados acima do texto do artigo.

## Captura de Tela

Para este artigo, começando com uma imagem de uma perereca verde com 1024 pixels de largura, foram feitas duas imagens menores com 128 e 256 pixels de largura. Nota: é melhor preparar as imagens na sua ferramenta de processamento de imagens favorita, como o *Gimp*. As imagens em tamanhos pequeno e médio foram usadas para criar as capturas de tela a seguir.

![Formulário de edição do artigo, aba de imagens e links](../../../en/images/articles/articles-edit-images-and-links-tab.png)

## Campos de Formulário

### Imagem de Introdução

- **Imagem de Introdução** Selecione uma imagem adequada para usar em layouts de Blog onde ela normalmente aparecerá acima do título do artigo. Isso é opcional. Se deixado em branco, não haverá Imagem de Introdução no layout do Blog.
- **Descrição da Imagem (Texto Alt)** Insira uma descrição de imagem adequada para leitores de tela.
- **Imagem Decorativa** Se não houver *Descrição da Imagem* e este botão não estiver marcado, a página não passará nos testes de acessibilidade. Se este botão estiver marcado, um atributo `alt` vazio será inserido. Isso pode permitir que a página passe nos testes de acessibilidade. Provavelmente é melhor sempre usar uma boa descrição curta da imagem.
- **Classe da Imagem** A classe padrão é *esquerda*, significando float-left. Mas qualquer outro valor de float aqui não terá efeito porque não pode ser usado em itens de grid ou flex.
- **Legenda da Imagem** As palavras inseridas aqui aparecerão como uma legenda abaixo da imagem. **Aviso:** Não use as mesmas palavras para o texto alt e a legenda. Leitores de tela anunciarão a informação duas vezes.
    - O texto alt deve fornecer uma descrição concisa do que está na imagem.
    - A legenda deve geralmente fornecer contexto para relacionar a imagem ao conteúdo circundante, ou chamar a atenção para uma informação particular.

### Imagem do Artigo Completo

Os mesmos campos da Imagem de Introdução, mas a imagem é usada em um contexto diferente. Veja as capturas de tela do Site abaixo.

### Link A

- **Link A** Cole o URL completo da página de destino. O URL completo deve ser usado, mesmo que a página de destino esteja neste site.
- **Texto do Link A** Digite o texto a ser usado para o link de destino.
- **Janela de Destino do URL** Escolha uma das opções de destino:
  - **Usar Global (Abrir na janela principal)**
  - **Abrir na janela principal** Este é o comportamento preferido porque o botão *Voltar* do navegador pode ser usado para voltar à página anterior.
  - **Abrir em nova janela** Alguns usuários gostam disso, mas confunde usuários móveis, pois não é óbvio que uma nova janela foi aberta e não há botão *Voltar*.
  - **Abrir em popup** Uma pequena janela popup aparece. A janela principal permanece disponível. Cada clique no link abre outra instância de janela popup.
  - **Abrir em modal** Um diálogo modal é aberto no centro da tela, que fica inativo até que a caixa de diálogo seja fechada.

### Links B e C

Exatamente a mesma entrada de dados que o Link A.

## Capturas de Tela do Site

A captura de tela abaixo mostra um layout de blog de categoria com a *Imagem de Introdução*. Poderia ter sido melhor usar uma imagem panorâmica com a mesma altura, mas com uma largura muito maior para ocupar o espaço branco vazio.

![Página de blog da categoria Anfíbios](../../../en/images/articles/articles-site-amphibians-blog.png)

A captura de tela abaixo mostra a página de artigo único com a *Imagem do Artigo Completo* e o Link A. A imagem foi alinhada à direita e a legenda visível diz algo para complementar o que a Descrição diz, de modo que soe lógico para leitores de tela.

![Página de artigo único de Sapos](../../../en/images/articles/articles-site-amphibians-frogs.png)

*Traduzido por openai.com*

