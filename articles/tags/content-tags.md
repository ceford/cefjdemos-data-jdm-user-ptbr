<!--
{
    "source": "https://docs.joomla.org/J4.x:How_To_Use_Content_Tags_in_Joomla",
    "title": "Tags de conte\u00fado",
    "description": " ",
    "author": ""
}
-->

## Introdução

As tags oferecem uma maneira fácil de usar e eficiente de organizar e exibir conteúdo. 
O **Componente de Tags** permite que tags individuais sejam usadas em diferentes 
tipos de conteúdo, incluindo artigos, categorias, contatos e feeds de notícias. Ele também permite a criação de tags pai e filhas.

Ao contrário das **Categorias** do Joomla, nas quais apenas uma categoria pode ser atribuída a
um item, várias tags podem ser atribuídas a um único item, mas não é
obrigatório atribuir tags aos itens.

Depois que um item é marcado com uma tag específica, clicar no botão da tag no
conteúdo que exibe tags levará você a uma página que exibe uma lista de
todos os itens marcados com aquela tag específica. Por esse
motivo, as tags são frequentemente usadas como uma forma de apresentar listas de conteúdo *filtradas*.

As tags podem ser adicionadas em vários locais, proporcionando flexibilidade na criação de tags.

## Considerações

Antes de começar, considere a finalidade das tags no site, especialmente
se outras pessoas adicionarão conteúdo. A menos que sejam adicionadas e gerenciadas
corretamente, as tags podem se tornar contraproducentes. Problemas comuns incluem
redatores adicionando novas tags desnecessárias e nomes de tags com erros de ortografia.
Alguns administradores do site podem optar por alterar as permissões de acesso para que
apenas usuários específicos possam adicionar novas tags.

A captura de tela a seguir mostra tags usadas em um site que contém artigos sobre
Sítios do Patrimônio Mundial da UNESCO. Nesse caso, cada tag tem uma cor distinta.

![a página da lista de tags](../../../en/images/tags/content-tags/01-tags-example.png)

Quando as tags são criadas, elas serão exibidas como links nos itens marcados.
Os estilos e as posições das tags são definidos pelo template do site. Elas geralmente
são estilizadas como botões ou rótulos.

A exibição de tags pode ser desativada para artigos individuais ou para todos os artigos! Isso
pode parecer ilógico, mas é um recurso útil quando as tags são usadas, por
exemplo, para filtrar conteúdo para casos de uso específicos.

## A lista de tags

- Selecione **Componentes → Tags** no menu do Administrador.

Esta captura de tela mostra tags em uma estrutura usada em um site multilíngue.
Cada idioma tem uma lista de tags com uma tag de idioma como pai.
A tag pai é usada nos módulos *Tags populares* e *Tags semelhantes*.

![a página da lista de tags](../../../en/images/tags/content-tags/02-tags-list.png)

Independentemente de como as tags são criadas, elas podem ser encontradas nesta lista.

- Selecione o botão **Novo** na barra de ferramentas para criar uma nova tag.
- Selecione um **Título** de tag para editar uma tag existente.

### A aba Detalhes da tag

![aba de opções do formulário de edição de tag mostrando classes CSS do Bootstrap](../../../en/images/tags/content-tags/03-edit-tag-details-tab.png)

- **Título** Este é o único campo *obrigatório*.
- **Apelido** Ele é criado a partir do Título ao salvar.
- **Descrição** É sempre melhor adicionar uma Descrição. Ela é exibida
  nos formulários do Administrador e pode ser útil quando muitas tags estão em uso.
- **Pai** Deixe definido como *Nenhum* se esta for uma tag que não tem pai. Ou escolha uma
  tag pai na lista para torná-la uma tag filha.
- **Status** Este campo é definido como *Publicado* por padrão. Ele pode ser definido como
  *Não publicado*, *Arquivado* ou *Lixeira*.
- **Acesso** O nível de acesso é Público por padrão.
- **Nota** e **Nota da versão:** Se necessário, você pode adicionar notas.
- **Salvar e fechar** Se você estiver criando várias tags, poderá selecionar **Salvar e novo** para criar uma nova tag.

### A aba Opções

- **Layout** Pode haver vários layouts disponíveis, e você pode criar seu próprio layout com uma substituição de template.
- **Classe CSS para o link da tag** Por padrão, as tags são exibidas como um botão azul. Você pode inserir declarações de classe aqui para personalizar a aparência das tags e dar cores diferentes a tags diferentes. Exemplo: `bg-danger-subtle border border-danger` são classes do Bootstrap que produzem um botão rosa com uma borda vermelha.
- **Imagem de chamada e imagem completa** Defina imagens para a tag — uma imagem de chamada para a lista de tags e/ou uma imagem completa para a página da tag.

![aba de opções do formulário de edição de tag mostrando classes CSS do Bootstrap](../../../en/images/tags/content-tags/04-edit-tag-options-tab.png)

### A aba Publicação

- Defina os metadados da página da tag para otimização para mecanismos de busca (SEO).

## Métodos alternativos de criação

### A partir de um artigo

É possível adicionar novas tags durante a criação ou edição de um artigo. Na
aba Conteúdo do artigo, no **Campo de tags**, insira o nome da nova tag e
pressione **Enter** para salvar e atribuir a tag ao artigo.

### A partir de uma categoria

As tags podem ser adicionadas durante a criação ou edição de uma categoria. Na aba **Categoria**,
insira o nome da tag no **Campo de tags** e pressione **Enter** para criar
e atribuir a nova tag.

### A partir de um contato

As tags podem ser adicionadas durante a criação ou edição de um contato. Na
aba **Novo/Editar contato**, insira o nome da tag no **Campo de tags** e pressione
**Enter** para criar e atribuir a nova tag. Você também pode adicionar novas tags ao criar categorias de contatos.

### A partir de um feed de notícias

As etiquetas podem ser adicionadas ao criar ou editar um novo feed de notícias. Na
aba **Novo/Editar feed de notícias**, insira o nome da etiqueta no **Campo de etiquetas** e pressione
**Enter** para criar e atribuir a nova etiqueta. Você também pode adicionar novas etiquetas ao
criar categorias de feeds de notícias.

## Gerenciando etiquetas

Sempre que você adicionar novas etiquetas no Joomla, todas elas aparecerão na lista de etiquetas.
Use a lista de etiquetas para encontrar, abrir e ajustar as configurações das etiquetas.

Você pode manipular a lista de várias maneiras:

- Pesquise uma etiqueta usando parte ou todo o seu título ou alias no campo de pesquisa.
- Reordene a lista usando arrastar e soltar para otimizar a ordem de exibição.
- Publique ou despublique etiquetas usando o botão na coluna Status.
- Selecione uma ou mais etiquetas e use o botão **Ações** para Publicar, Despublicar,
  Arquivar, Fazer check-in ou Mover para a lixeira as etiquetas selecionadas.
- Selecione uma ou mais etiquetas e use o botão **Ações → Lote** para definir o
  Idioma ou o Nível de acesso.

## Exibição das etiquetas

Depois que as etiquetas forem criadas em seu site, elas estarão disponíveis para uso no conteúdo e em módulos como **Etiquetas populares** e **Etiquetas semelhantes**. Os exemplos a seguir mostram como elas podem aparecer em um site que usa o template padrão **Cassiopeia**.

![etiquetas exibidas em um artigo e nos módulos de etiquetas populares e etiquetas semelhantes](../../../en/images/tags/content-tags/05-tag-modules-site-view.png)

Ao selecionar uma das etiquetas, você será levado a uma página que lista
todos os itens atribuídos àquela etiqueta específica:

![exemplo de uso de etiquetas no site com labrador preto](../../../en/images/tags/content-tags/06-items-with-cultural-site-tag.png)

A lista de itens é uma lista filtrada do conteúdo do site com a etiqueta selecionada.
Uma caixa de filtro é fornecida para facilitar a localização de itens à medida que a lista cresce.
Você também pode definir o número de resultados que deseja ver em uma única visualização.

## Configuração das etiquetas

As etiquetas individuais herdam as configurações das opções do componente Etiquetas. Selecione o
botão **Opções** na barra de ferramentas da página da lista de etiquetas para ver as opções padrão de
etiquetas disponíveis.

As opções de configuração do componente Etiquetas podem ser substituídas nos níveis do item de conteúdo e/ou do item de menu.

## Dicas

- Lembre-se de que as etiquetas são usadas em vários tipos de conteúdo.
- Você pode adicionar mais de uma etiqueta a um item.
- Use o botão Ajuda da barra de ferramentas quando tiver dúvidas.

*Traduzido por openai.com*