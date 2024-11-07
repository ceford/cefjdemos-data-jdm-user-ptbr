<!-- Filename: J4.x:How_To_Use_Content_Tags_in_Joomla / Display title: Tags de Conteúdo  -->

## Introdução

As tags oferecem uma maneira fácil e eficiente de organizar e exibir conteúdo. O **Componente de Tags** permite que tags sejam usadas em diferentes tipos de conteúdo, incluindo artigos, categorias, contatos e feeds de notícias. Ele também fornece a criação de tags de pai e filho.

Ao contrário das **Categorias** do Joomla, onde apenas uma categoria pode ser atribuída a um item, várias tags podem ser atribuídas a um único item, mas não é um requisito atribuir tags aos itens.

Uma vez que um item é marcado com uma tag específica, clicar no botão da tag em conteúdos que exibem tags o levará a uma página que exibe uma lista de todos os itens que foram marcados com aquela tag em particular. Por essa razão, as tags são frequentemente usadas como uma forma de apresentar listas *filtradas* de conteúdo.

As tags podem ser adicionadas em vários lugares, proporcionando flexibilidade na criação de tags.

## Considerações

Antes de começar, considere o propósito das tags no site, especialmente se outras pessoas forem adicionar conteúdo. A menos que sejam adicionadas e gerenciadas corretamente, as tags podem se tornar contraproducentes. Problemas comuns incluem redatores de conteúdo adicionando novas tags desnecessárias e nomes de tags com erros ortográficos. Alguns administradores do site podem optar por alterar as permissões de acesso para que apenas usuários específicos possam adicionar novas tags.

Quando as tags são criadas, elas serão exibidas como links nos itens marcados. Os estilos e posições das tags são definidos pelo modelo do site. Frequentemente, são estilizadas como botões ou rótulos.

A exibição das tags pode ser desativada! Isso pode parecer ilógico, mas é um recurso útil quando as tags são usadas, por exemplo, para filtrar o conteúdo para casos de uso específicos.

## A Lista de Tags

- Selecione **Componentes → Tags** no menu do Administrador.

![a página da lista de tags](../../../en/images/tags/tags-list.png)

Independentemente de como as tags são criadas, elas podem ser encontradas nesta lista.

## Adicionando Tags

### Através da Lista de Tags

Selecione o botão **Novo** na barra de ferramentas da lista de Tags.

![nova tag chamada predator](../../../en/images/tags/new-tag-predator.png)

- **Título** Este é o único campo *obrigatório*.
- **Nome alternativo** Este é criado a partir do Título ao salvar.
- **Descrição** É sempre melhor adicionar uma Descrição. Ela é exibida em formulários
  do Administrador e pode ser útil quando muitas tags estão em uso.
- **Pai** Deixe configurado como *Nenhum* se for uma tag pai raiz. Ou escolha uma
  tag pai da lista se for uma tag filho.
- **Status** Este campo está configurado como *Publicado* por padrão. Pode ser definido como 
  *Não publicado*, *Arquivado* ou *Excluído*.
- **Acesso** O nível de acesso é Público por padrão.
- **Nota** e **Nota da Versão:** Se necessário, você pode adicionar notas.
- **Salvar & Fechar** A nova tag aparecerá na Lista de Tags. Se você estiver
  criando várias tags, pode optar por clicar em **Salvar & Novo** para 
  criar outra.

Uma vez salva, a tag estará disponível para uso em vários tipos de conteúdo que a utilizam.

### Dentro de um Artigo

É possível adicionar novas tags enquanto cria ou edita um artigo. No
guia de Conteúdo do artigo, no campo **Tags**, insira o nome da nova tag e
pressione **Enter** para salvar e atribuir a tag ao artigo.

### Dentro de uma Categoria

Tags podem ser adicionadas ao criar ou editar uma categoria. No guia 
**Categoria**, insira o nome da tag no campo **Tags** e pressione **Enter**
para criar e atribuir a nova tag.

### Dentro de um Contato

Tags podem ser adicionadas ao criar ou editar um Contato. Na guia 
**Novo/Editar Contato**, insira o nome da tag no campo **Tags** e pressione
**Enter** para criar e atribuir a nova tag. Você também pode adicionar novas tags ao criar
Categorias de Contato.

### Dentro de um Feed de Notícias

Tags podem ser adicionadas ao criar ou editar um novo Feed de Notícias. Na 
guia **Novo/Editar Feed de Notícias**, insira o nome da tag no campo **Tags** e pressione
**Enter** para criar e atribuir a nova tag. Você também pode adicionar novas tags ao 
criar Categorias de Feed de Notícias.

## Gerenciando Tags

Sempre que você adicionar novas Tags no Joomla, elas aparecerão todas na lista de Tags.
Utilize a lista de Tags para encontrar, abrir e ajustar as configurações das tags.

### O Filtro da Lista de Tags

![filtro de lista de tags por tipo](../../../en/images/tags/tags-list-filter.png)

Você pode manipular a lista de várias maneiras:

- Pesquise uma tag utilizando parte ou todo o seu título no campo de pesquisa.
- Reordene a lista usando arrastar e soltar para otimizar a ordem de exibição.
- Publique ou Despublique tags usando o botão na coluna Status.
- Selecione uma ou mais tags e use o botão **Ações** para Publicar, Despublicar, Arquivar, Fazer check-in ou Mover para a Lixeira as tags selecionadas.
- Selecione uma ou mais tags e use o botão **Ações → Lote** para definir o idioma ou o Nível de Acesso.

### Configurações de Tag

- Selecione um **Título** de tag para fazer alterações em suas configurações.

No formulário de edição da tag:

- As configurações da aba **Detalhes da Tag** foram cobertas acima.
- A aba **Opções**:
  - Altere o layout da página da tag (a página que aparece quando você clica no link da tag - por exemplo, meusite.com/tags/minha-tag). Este layout é normalmente o padrão e depende do template.
  - Adicione uma Classe CSS para aplicar um estilo (aparência) diferente ao link da tag. Isto normalmente seria usado apenas pelo Administrador do Site.
  - Defina imagens para a tag - uma imagem de teaser para a lista de tags e/ou uma imagem completa para a página da tag.
- A aba **Publicação**: Defina Metadados para a página da tag para Otimização para Motores de Busca (SEO).

## Como o Joomla Exibe Tags

Uma vez que as tags foram criadas em seu site, elas estão disponíveis para uso não apenas em conteúdo, mas também em alguns módulos úteis, como **Tags Populares** e **Tags Similares**. Os exemplos a seguir mostram como eles aparecem em uma instalação padrão usando o Template padrão **Cassiopeia**.

![exemplo de uso de tags no site labrador amarelo](../../../en/images/tags/tag-examples-yellow-labrador.png)

Quando você clica em uma das tags, será levado para uma página que lista todos os itens atribuídos a essa tag específica:

![exemplo de uso de tags no site labrador preto](../../../en/images/tags/tag-examples-black-labrador.png)

Clicar em uma tag levará você a uma página que exibe uma lista de todos os itens atribuídos a essa tag específica - na prática, é uma lista filtrada do conteúdo com tags do seu site. Uma caixa de filtro é fornecida para facilitar a busca por itens à medida que a lista cresce. Você também pode definir o número de resultados que deseja ver em uma única visualização.

## Configuração de Tags

Tags individuais herdam configurações das opções do componente de Tags. Isso é abordado em um tutorial separado. [ToDo] Selecione o botão **Opções** na barra de ferramentas da página da lista de Tags.

A configuração do componente de Tags pode ser substituída no nível do item de menu.

## Dicas

- Lembre-se de que as Tags são usadas em vários tipos de conteúdo
- Você pode adicionar mais de uma Tag a um item
- Use o botão de Ajuda quando estiver em dúvida

*Traduzido por openai.com*

