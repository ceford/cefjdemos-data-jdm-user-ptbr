<!-- Filename: Smart_Search_content_change_test_plan / Display title: Plano de Teste de Busca Inteligente -->

O seguinte é um plano de teste preliminar que cobre (principalmente) a atualização do índice de Busca Inteligente quando ocorrem vários tipos de atualizações de conteúdo.

A Busca Inteligente precisa ser testada para cada um dos tipos de conteúdo principais suportados. Estes são:

- Artigos
- Categorias
- Contatos
- Feeds de notícias
- Links da web

Para cada um dos tipos de conteúdo acima, precisamos testar o seguinte:

## Mudanças no Texto

Alterar vários campos de texto dentro de um item de conteúdo deve alterar os termos de busca no índice (com uma exceção notável descrita abaixo). Não há necessidade de testar todos os campos de texto para um dado tipo de conteúdo, já que, se funcionar para um, funcionará para todos, então basta escolher um para cada tipo de conteúdo. Os seguintes campos de texto são indexados para os componentes principais:

- Artigos
  - Título
  - Aliás
  - Texto do artigo
  - Descrição dos metadados
  - Palavras-chave dos metadados
  - Autor dos metadados
  - Autor
  - Criado por aliás
- Categorias
  - Título
  - Aliás
  - Descrição
  - Link ??? (não tenho certeza se existe tal campo)
  - Descrição dos metadados
  - Palavras-chave dos metadados
  - Autor dos metadados
  - Autor
- Contatos
  - Nome
  - Aliás
  - Nome de usuário vinculado
  - Outras informações
  - Posicionamento (se habilitado nas Opções)
  - Endereço (se habilitado nas Opções)
  - Cidade (se habilitado nas Opções)
  - Região (se habilitado nas Opções)
  - País (se habilitado nas Opções)
  - CEP (se habilitado nas Opções)
  - Telefone (se habilitado nas Opções)
  - Fax (se habilitado nas Opções)
  - Email (se habilitado nas Opções)
  - Celular (se habilitado nas Opções)
  - Página da web (se habilitado nas Opções)
- Feeds de notícias
  - Título
  - Aliás
  - Link
  - Descrição dos metadados
  - Palavras-chave dos metadados
  - Autor dos metadados
  - Autor
  - Criado por aliás
- Links da web
  - Título
  - Aliás
  - URL
  - Descrição
  - Descrição dos metadados
  - Palavras-chave dos metadados
  - Autor dos metadados
  - Autor
  - Criado por aliás

Para testar, simplesmente adicione uma string aleatória, como "xyz", entre um monte de texto comum e próximo ao topo, e então tente buscar esse termo no front-end.

- sua string aleatória deve aparecer na lista de autocompletar enquanto você a digita.
- sua string aleatória deve aparecer 3 vezes na lista de autocompletar.
  - por si só
  - junto com a próxima palavra que a segue
  - junto com as próximas 2 palavras que a seguem
- o item de conteúdo com sua string aleatória deve aparecer na lista de resultados de busca.
- sua string aleatória deve estar destacada nos resultados de busca, desde que você a tenha inserido perto do topo do texto (porque o texto nos resultados é truncado).

Remova sua string aleatória do texto: Isso deve remover os 3 termos/frases de busca do índice. Buscar por qualquer um dos 3 termos de busca não deve produzir resultados.

Excluir o item de conteúdo: Isso removerá todos os termos/frases de busca utilizados no item de conteúdo do índice, exceto onde esses termos/frases de busca ainda são utilizados em outros itens de conteúdo.<sup>[\[1\]](#cite_note-1)</sup>

O item de conteúdo excluído não deve aparecer em nenhuma lista de resultados de pesquisa.

## Mudanças de estado do item de conteúdo

Encontre um item de conteúdo do tipo necessário usando a Busca Inteligente. Em seguida, faça
estes testes:

- Mova o item para a lixeira e repita a busca. O item não deve mais aparecer
  nos resultados da busca.
- Publique o item novamente e repita a busca. O item deve aparecer
  nos resultados da busca novamente.
- Despublique o item e repita a busca. O item não deve mais
  aparecer nos resultados da busca.
- Arquive o item e repita a busca. O item deve aparecer
  nos resultados da busca novamente.

## Alterações no mapa de conteúdo (taxonomia)

Embora alterações na categoria sejam um caso especial de mudanças no mapa de conteúdo, também precisamos testar alterações em ramos do mapa de conteúdo que não são categorias, porque mudanças nas categorias exercitam alguns códigos diferentes. Estes são os campos que não são de categoria e estão sujeitos aos mapas de conteúdo nos componentes principais:

- Artigos
  - Autor
  - Categoria
  - Idioma
- Contatos
  - Categoria
  - País
  - Idioma
  - Região
- Feeds de notícias
  - Categoria
  - Idioma
- Links da web
  - Categoria
  - Idioma

Então, escolha um (se um funcionar, todos funcionarão para aquele tipo de conteúdo) dos acima que seja apropriado para o tipo de conteúdo e verifique se:

- mudar o campo resulta no item aparecendo em uma busca usando o menu 
  suspenso relevante (na busca avançada) para o campo que você alterou. 
  <sup>[\[2\]](#cite_note-2)</sup>
- o item de conteúdo não aparece em uma busca usando o valor antigo do 
  campo.

Exclua o item de conteúdo e verifique se ele não aparece mais nos resultados de busca usando o filtro drop-down relevante. Observe que **não** é esperado que um nó não utilizado seja removido do menu suspenso do filtro relevante. <sup>[\[3\]](#cite_note-3)</sup>

## Alterações de estado da categoria

Alterar o estado da categoria à qual um item pertence deve atualizar o índice para esse item. Além disso, mudar o estado de uma categoria pai da categoria à qual um item pertence também deve atualizar o índice para esse item. Para testar, encontre ou crie um item com a seguinte estrutura:

    Categoria A contendo Categoria A.1 contendo item de conteúdo

Mude o status da Categoria A.1 e teste da seguinte forma:

- Mova a Categoria A.1 para a lixeira e repita a pesquisa. O item não deve mais aparecer nos resultados da pesquisa.
- Publique a Categoria A.1 novamente e repita a pesquisa. O item deve aparecer novamente nos resultados da pesquisa.
- Despublique a Categoria A.1 e repita a pesquisa. O item não deve mais aparecer nos resultados da pesquisa.
- Arquive a Categoria A.1 e repita a pesquisa. O item deve aparecer novamente nos resultados da pesquisa.

Restaure a Categoria A.1, depois altere o status da Categoria A e teste da seguinte forma:

- Mova a Categoria A para a lixeira e repita a pesquisa. O item não deve mais aparecer nos resultados da pesquisa.
- Publique a Categoria A novamente e repita a pesquisa. O item deve aparecer novamente nos resultados da pesquisa.
- Despublique a Categoria A e repita a pesquisa. O item não deve mais aparecer nos resultados da pesquisa.
- Arquive a Categoria A e repita a pesquisa. O item deve aparecer novamente nos resultados da pesquisa.

## Alterações no nível de acesso ao item de conteúdo

Altere o nível de acesso de um item de conteúdo para algo que um usuário final não deveria conseguir ver.

- verifique se o item de conteúdo não aparece nas listas de resultados de pesquisa.

Altere o nível de acesso de volta para algo que um usuário final deveria conseguir ver.

- verifique se o item de conteúdo agora aparece nas listas de resultados de pesquisa.

Observe que termos de pesquisa dentro do item de conteúdo ainda aparecerão na lista de autocompletar, mesmo que o usuário não tenha acesso ao próprio item de conteúdo. Este é um comportamento esperado, embora possa ser algo que queiramos analisar. <sup>[\[4\]](#cite_note-4)</sup>

## Alterações no nível de acesso da categoria

Alterar o nível de acesso da categoria à qual um item pertence deve atualizar o índice para esse item. Além disso, alterar o nível de acesso de uma categoria mãe da categoria à qual um item pertence também deve atualizar o índice para esse item. Para testar, encontre ou crie um item com a seguinte estrutura:

    Categoria A contendo Categoria A.1 contendo item de conteúdo

Realize os seguintes testes:

- Altere o nível de acesso da Categoria A.1 para algo que um usuário do front-end não deveria ser capaz de ver.
  Verifique se o item de conteúdo não aparece nas listas de resultados de pesquisa.
- Altere o nível de acesso da Categoria A.1 de volta para algo que um usuário do front-end deveria ser capaz de ver.
  Verifique se o item de conteúdo agora aparece nas listas de resultados de pesquisa.
- Altere o nível de acesso da Categoria A para algo que um usuário do front-end não deveria ser capaz de ver.
  Verifique se o item de conteúdo não aparece nas listas de resultados de pesquisa.
- Altere o nível de acesso da Categoria A de volta para algo que um usuário do front-end deveria ser capaz de ver.
  Verifique se o item de conteúdo agora aparece nas listas de resultados de pesquisa.

## Alterações de estado do Smart Search

Na tela Administrador → Componentes → Smart Search → Mapas de Conteúdo, é possível alterar o estado de publicação/despublicação de ramos e nós do mapa de conteúdo. Os seguintes testes devem ser realizados:

- Despublicar um ramo do mapa de conteúdo (ex. Autor). Verifique se o menu suspenso de filtro para esse ramo não está mais visível na pesquisa avançada.
- Despublicar um nó do mapa de conteúdo (dentro de um ramo publicado). Por exemplo, "Animais" dentro do ramo "Categoria". Verifique se o nó não está listado no menu suspenso de filtro para o ramo na pesquisa avançada.

Na tela Administrador → Componentes → Smart Search → Conteúdo Indexado, realize o seguinte teste:

- Despublicar um item de conteúdo. Verifique se o item de conteúdo não aparece mais nos resultados de pesquisa.

Na tela Administrador → Extensões → Gerenciador de Plugins, realize o seguinte teste:

- Defina o filtro "Selecionar tipo" para "finder" ou "smart search".
- Escolha um dos plugins de tipo de conteúdo e despublique-o. Todos os dados para esse tipo de conteúdo devem ser removidos do índice.

Nota: Se você publicar o plugin novamente, ele não adicionará os dados de volta ao índice. Este é o comportamento esperado. Você precisará executar o indexador novamente para recuperar os dados.

*Traduzido por openai.com*

