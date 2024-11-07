<!-- Filename: J4.x:Create_and_Manage_Article_Categories / Display title: Artigos: Categorias  -->

## Introdução

Imagine uma biblioteca sem um sistema de classificação: os livros são simplesmente colocados nas prateleiras na ordem em que são recebidos. Isso não é muito útil se a biblioteca tiver milhões de livros e você estiver procurando por algo sobre História, Jardinagem ou Ciência. O mesmo tipo de argumento se aplica a Artigos. Se você tiver dezenas, centenas ou milhares de artigos, realmente precisa de um método para classificá-los, de modo que possa encontrar facilmente o que precisa. É para isso que servem as Categorias.

Uma categoria no Joomla! pode conter tanto artigos quanto subcategorias em uma estrutura em forma de árvore, aninhada em qualquer profundidade, embora seja improvável que você deseje ir além de uma profundidade de três ou quatro. Por exemplo, se seus artigos são sobre Natureza, você pode classificá-los da seguinte forma:

- Animais
  - Aves
    - Falcões
    - Tentilhões
    - Gaivotas
  - Mamíferos
    - Primatas
    - Macacos
    - Roedores
- Plantas
  - Flores
    - Margaridas
    - Rosas
  - Árvores
    - Carvalhos
    - Ulmeiros

Neste exemplo, a categoria *Animais* pode conter artigos sobre animais em geral, bem como subcategorias para artigos sobre diferentes tipos de animais.

Joomla fornece uma categoria padrão única chamada Sem Categoria. Qualquer artigo não atribuído a uma categoria específica que você tenha criado se torna membro da categoria Sem Categoria. Você cria categorias conforme necessário para adequar à natureza dos seus artigos.

Um artigo só pode pertencer a uma categoria. Em algumas circunstâncias, isso não é suficiente. Suponha, por exemplo, que você deseje procurar livros de todos os tipos escritos em um idioma específico, ou todas as plantas que são venenosas ou todos os animais que são perigosos. É aí que as Tags são úteis. Elas são abordadas em outro lugar.

### Usando Categorias

Na página de *Artigos* no administrador, o formulário de *Opções de Filtro* tem uma lista suspensa **- Selecione Categoria -** que exibe uma árvore de categorias permitindo que você filtre artigos em uma Categoria selecionada. Você também pode criar tipos de itens de menu *Blog de Categoria* e *Lista de Categoria* para exibir artigos de uma categoria selecionada para os visitantes do site.

## Adicionando Categorias e Subcategorias

Existem várias maneiras de chegar à página *Artigos: Nova Categoria*:

- Pelo **Painel Inicial**: Selecione o **símbolo de mais (+)** à direita do link *Categorias de Artigos*. Este último leva à página de lista *Artigos: Categorias*.
- Pelo **Menu do Administrador**: Selecione o item *Conteúdo* para expandir a lista e, em seguida, selecione o **símbolo de mais (+)** à direita do link *Categorias*.
- Pelo **Painel de Conteúdo**: Selecione o ícone do Painel à direita do link *Conteúdo* no menu do Administrador e, em seguida, no painel de *Conteúdo* do painel selecione o **símbolo de mais (+)** à direita do link *Categorias*.
- Via **Artigos: Categorias**: Siga qualquer uma das rotas para a página de lista e selecione o botão **Novo** na Barra de Ferramentas.

A captura de tela a seguir mostra o link *Categorias de Artigos* no Painel Inicial para a lista de categorias e o *Símbolo de Mais* adjacente que leva ao formulário *Artigos: Nova Categoria*.

![O ícone de adicionar categoria destacado no painel inicial](../../../en/images/articles/category-add-via-home-dashboard.png)

## Os Artigos: formulário de Nova Categoria

![O formulário de edição da nova categoria de artigos](../../../en/images/getting-started/article-category-edit.png)

A captura de tela acima mostra o formulário preenchido. Existem apenas dois campos que precisam de algum conteúdo. Todo o resto tem valores padrão ou nulos que você pode deixar por enquanto e preencher mais tarde conforme a necessidade surgir.

- **Título** Este é o único campo obrigatório. Ele deve ser curto, mas descritivo da categoria.

### A aba Categoria

- **Descrição** Embora não seja obrigatório, este campo pode ser exibido em páginas de lista de categorias do site controladas por itens de menu. Talvez você precise voltar e atualizar a Descrição mais tarde.
- **Pai** Se definido como *- Sem pai -*, este novo item é uma categoria pai em potencial para outras categorias. Se outra categoria for selecionada como pai, este novo item é uma subcategoria.
- **Status** Por padrão, uma nova categoria é definida como *Publicado*. Você pode mudar o status de uma categoria para *Publicado*, *Não publicado*, *Arquivado* ou *Excluído*.
  [A Fazer] Explique o que acontece quando uma Categoria não está publicada...
- **Acesso** Por padrão, o acesso é definido como *Público*. Outras opções para restringir o acesso são *Visitante*, *Registrado*, *Especial* e *Super Usuários*.
  [A Fazer] Explique como o Acesso a uma Categoria pode ser usado...
- **Idioma** Em sites multilíngues, definir isto como *Todos* tornará a nova categoria independente do Idioma do site. Se definido para um idioma específico, ela estará disponível apenas em páginas que usam esse idioma.
- **Tags** Se você as usar, pode adicionar uma ou mais tags à categoria. Definir tags no nível de categoria é uma boa maneira de manter a consistência. Para este tutorial, uma tag *Natureza* foi criada e usada para filtrar listas que mostram apenas itens relacionados aos tutoriais.
- **Nota** e **Nota de Versão** Use estes para adicionar notas relevantes, se necessário.

### A aba Opções

As configurações nesta aba afetam a aparência desta Categoria nas páginas do site.

- **Layout** Refere-se ao posicionamento do conteúdo na página. Pode haver uma escolha de layouts dependendo do componente e do template em uso.
  [A Fazer] Exemplos...
- **Imagem** Você pode querer usar uma imagem para atuar como um ícone para que esta categoria possa ser instantaneamente reconhecida em uma lista de categorias. Se usado para tal propósito, uma *Descrição de Imagem (Texto Alt)* não é necessária, mas a caixa de seleção *Sem Descrição* deve ser marcada.

### Salvar & Fechar

- **Salvar & Fechar** Para finalizar a edição desta categoria. Ou na lista suspensa...
  - **Salvar & Novo** Salve esta categoria e abra um novo formulário de edição para uma nova categoria. Por exemplo, você pode querer começar a construir uma árvore de categorias adicionando uma categoria *Primatas* com *Mamíferos* como seu pai.
  - **Salvar no Menu como Lista** ...
  - **Salvar no Menu como Blog** ...
  - **Salvar como Cópia** ...

Fechar o formulário de edição leva à página de lista **Artigos: Categorias**.

![Uma lista de categorias filtrada pela tag Natureza](../../../en/images/articles/categories-list.png)

### Salvar no Menu como Lista

A seleção deste item na lista suspensa *Salvar & Fechar* salvará e fechará o formulário de edição de categoria e abrirá um novo formulário de item de menu com todos os dados necessários para criar uma *Lista de Categoria* para esta categoria. Você pode querer mudar o *Título*. Por exemplo, poderia ser *Lista de Artigos de Mamíferos* para deixar claro que é provável que seja uma lista de artigos.

Na aba *Exibir Página*, tente definir o campo *Mostrar Cabeçalho da Página* como *Mostrar*. Isso mostra *Lista de Artigos de Mamíferos* como um cabeçalho em negrito no topo da página, dando uma aparência geral mais completa.

### Salvar no Menu como Blog

A seleção deste item na lista suspensa *Salvar & Fechar* salvará e fechará o formulário de edição de categoria e abrirá um novo formulário de item de menu com todos os dados necessários para criar um *Blog de Categoria* para esta categoria. Você pode querer mudar o *Título*. Por exemplo, poderia ser *Blog de Artigos de Mamíferos* para que os últimos artigos sobre mamíferos sejam destacados.

Na aba *Exibir Página*, tente definir o campo *Mostrar Cabeçalho da Página* como *Mostrar*. Isso mostra *Blog de Artigos de Mamíferos* como um cabeçalho em negrito no topo da página, dando uma aparência geral mais completa.

A seguinte captura de tela mostra a visualização do site de uma página de blog de categoria em desenvolvimento.

![Página de blog da categoria Mamíferos](../../../en/images/articles/article-mammals-articles-blog-site-view.png)

## Dicas

- Você também pode criar categorias de artigos dentro de um artigo.
- Lembre-se de que você só pode atribuir um artigo a uma categoria.
- Como tanto as categorias principais quanto as subcategorias podem ter
  subcategorias adicionais, planeje e organize as categorias com cuidado. 
  Uma hierarquia de categorias complicada pode se tornar um desafio para gerenciar.
- Outro método de agrupar conteúdo no Joomla é o uso do Componente 
  **Tags**, que permite adicionar várias tags aos seus artigos. 
  Usar categorias e tags pode ajudar a minimizar o número de 
  subcategorias e fornecer uma maneira eficiente de estruturar o 
  conteúdo do site e oferecer aos visitantes mais recursos para navegar 
  pelo conteúdo do site.

*Traduzido por openai.com*

