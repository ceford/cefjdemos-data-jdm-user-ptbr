<!-- Filename: J4.x:Submenus / Display title: Submenus -->

## Noções Básicas de Menu

No Joomla, três elementos contribuem para a exibição de um menu ao
usuário:

- Um Menu é um contêiner para itens de menu.
- Um Item de Menu é um link para uma página do site ou página externa.
- Um Módulo de Menu fornece um método para alocar o menu a uma posição
  na página e controlar aspectos da aparência ou comportamento do menu ou da página.

Menus simples consistem em listas de links. Às vezes, membros de uma lista têm relações de pai e filho, exibidas como filhos indentados ou listas suspensas. Relações de pai e filho podem ser aninhadas em qualquer nível. No entanto, aninhamento além de dois níveis pode tornar as listas pouco atraentes e complicadas de usar.

Há ocasiões em que você pode querer mostrar os filhos de um menu pai como um submenu separado. Um caso comum de uso é mostrar um submenu à esquerda de uma página, o conteúdo da página no centro e um índice da página à direita. Este tutorial explica como fazer isso.

### Dados de Exemplo

Suponha que você tenha uma série de artigos sobre animais. Podem ser animais de estimação, uma ficha de informações veterinárias ou um zoológico. A seguir está uma estrutura curta de exemplo para fins de demonstração:

    Animais
        Gatos
            Birmanês
            Azul Russo
        Cães
            Collies
            Pomerânia

As listas podem ser bastante longas, então você pode querer exibir apenas uma lista de raças de gatos nas páginas sobre gatos e apenas uma lista de raças de cães nas páginas sobre cães. A captura de tela a seguir mostra o layout pretendido que o usuário gostaria de alcançar:

![submenus objetivos animais gatos](../../../en/images/menus/submenus-objectives-animals-cats.png)

Neste exemplo, quando o usuário seleciona o item de menu Animais, a página Animais é carregada e o módulo de menu Gatos desaparece (nem o módulo Cães aparece). Selecionar o item de menu Gatos faz com que o módulo de menu Gatos apareça junto à página Gatos. Selecionar o item de menu Birmanês faz com que a página Birmanês apareça. Selecionar o item de menu Cães substitui o módulo de menu Gatos por um módulo de menu Cães junto à página Cães.

Para tentar este tutorial por conta própria, você precisará criar alguns artigos, um menu com itens de menu e três módulos de menu.

## Criar Artigos

Se você é super eficiente, pode criar um artigo e, em seguida, criar um item de menu a partir do artigo. Para isso, primeiro seria necessário criar um novo menu e tomar algumas etapas extras durante a criação do artigo. Portanto, é melhor manter as coisas simples inicialmente e começar com seus novos artigos:

- Selecione **Conteúdo** → **Artigos** → **+** no menu do Administrador.
  Ou selecione o botão `Novo` na lista de Artigos.
- Preencha o formulário como faria com qualquer artigo.
- Selecione o botão `Salvar & Novo` do `Salvar & Fechar` para passar para
  o próximo novo artigo.

Os dados de exemplo mostrados acima requerem sete artigos.

## Criar um Novo Menu

No menu do Administrador:

- Selecione **Menus** → **Gerenciar**.
- Na página de lista de Menus, selecione o botão `Novo` para criar um novo menu.
- No formulário Menus: Adicionar, dê ao menu um título: Animais e um nome único: animais.
- Em alguns casos, pode ser necessário lembrar do objetivo deste menu. Portanto, preencha o campo de descrição.
- Salvar ou Salvar & Fechar.

![submenus novo menu](../../../en/images/menus/submenus-new-menu.png)

## Criar Itens de Menu

Há sete itens de menu para criar.

### Item de Menu Animais

Os novos itens de menu estarão localizados no menu Animais.

- Selecione **Menus** → **Animais** → **+** no menu do Administrador.
- Preencha o formulário Menu: Editar Item.
  - Título: Animais
  - Tipo de Item de Menu: Artigo Único
  - Selecionar Artigo: Animais - este é o artigo pai utilizado para
    introduzir a série sobre Animais
  - Menu: Animais
  - Pai: - Sem Pai - esta é a raiz do menu
- Selecione **Salvar & Novo** na lista suspensa `Salvar & Fechar`.

### Item de Menu Gatos

Este é, em grande parte, uma repetição do item de menu Animais. Exceto:

- O título deve ser Gatos.
- O artigo selecionado no campo Selecionar Artigo deve ser `Gatos`.
- O Item Pai deve ser configurado como `Animais`.

### Item de Menu Birmanês

Repita novamente. Exceto:

- O título deve ser Birmanês.
- O artigo selecionado no campo Selecionar Artigo deve ser `Birmanês`.
- O Item Pai deve ser configurado como `Gatos`.

### Mais Itens de Menu

Continue até que você tenha sete itens de menu, um para cada artigo.  

## Lista de Itens do Menu

Quando você tiver criado todos os seus itens de menu, verifique se eles apresentam as relações corretas de pai-filho e se estão na ordem correta. Você pode ordenar a coluna de Ordenação (a segunda coluna) e usar os controles de arrasto (elipses verticais) para mover os itens para a ordem correta. Se algum item tiver um pai incorreto, basta selecionar o título do item e mudar o pai no formulário Menus: Editar Item.

![lista de itens do menu de submenus](../../../en/images/menus/submenus-menu-items-list.png)

## Módulos de Menu

Nesta fase, você tem um menu, mas ele não possui um módulo para ser atribuído a uma posição na página. Você poderia usar o menu inteiro como um menu padrão ou um menu suspenso. No entanto, o objetivo deste tutorial é demonstrar como criar submenus. Para isso, você precisará de três módulos diferentes:

- Um módulo Animais para um submenu com itens de menu sobre Animais, Gatos e Cachorros.
- Um módulo Gatos para um submenu com itens de menu sobre raças de gatos.
- Um módulo Cachorros para um submenu com itens de menu sobre raças de cachorros.

## Módulo de Submenu de Animais

No menu do Administrador:

- Selecione **Conteúdo** → **Módulos do Site** → **+** ou selecione `Novo` na lista de
  Módulos (Site).
- Selecione o módulo **Menu**.
- No formulário de edição do Módulo: Menu, insira os seguintes dados:
  - Título: Animais
  - Selecionar Menu: Animais
  - Item Base: Animais (este é o item de menu pai)
  - Nível Inicial: 1
  - Nível Final: 2 (isso limita os itens aos itens de menu em Gatos e
    Cães)
  - Posição: barra lateral-esquerda (ou onde for mais adequado)

![módulo de submenus animais](../../../en/images/menus/submenus-animals-module.png)

### Atribuição de Menu de Animais

Submenus são normalmente exibidos apenas em páginas onde são relevantes,
neste caso em apenas três páginas. Na aba Atribuição de Menu:

- Defina o campo Atribuição de Módulo para `Somente nas páginas selecionadas`. Isso
  revela uma lista hierárquica de todos os itens em todos os menus.
- Marque as caixas para Animais, Gatos e Cães.
- Marque as caixas para as raças de gatos e cães. Caso contrário, o
  submenu Animais desaparecerá em páginas sobre raças.
- Certifique-se de que nenhuma outra caixa esteja marcada.
- Salvar & Fechar

![atribuição de menu módulo animais de submenus](../../../en/images/menus/submenus-animals-module-menu-assignment.png)

## Módulo de Submenu de Gatos

Isso é muito semelhante:

- Selecione **Conteúdo**→**Módulos do Site**→**+** ou selecione `Novo` na lista de Módulos (Site).
- Selecione o módulo **Menu**.
- No formulário de edição de Módulos: Menu, insira os seguintes dados:
  - Título: Gatos
  - Selecionar Menu: Animais
  - Item Base: Gatos (este é o item de menu pai)
  - Nível Inicial: 3
  - Nível Final: Todos
  - Posição: barra lateral-esquerda (ou em outro lugar que lhe convier)

### Atribuição de Menu de Gatos

Na Atribuição de Menu

- Configure o campo de Atribuição do Módulo para `Apenas nas páginas selecionadas`. Isso revela uma lista hierárquica de todos os itens em todos os menus.
- Marque as caixas ao lado de Gatos, Burmese e Azul Russo. Certifique-se de que nenhuma outra caixa esteja marcada.
- Salvar & Fechar

## Módulo de Submenu de Cães

Mais do mesmo...

## Alias do Item de Menu

Até agora tudo bem! Mas não há um link para a página de Animais no Menu Principal ou em qualquer um dos outros menus do site. A maneira fácil de corrigir isso é com um Alias do Item de Menu. Neste exemplo, uma entrada é feita no menu na parte superior da página, intitulada Main Menu Blog. No menu do Administrador:

- Selecione **Menus** → **Main Menu Blog** (ou o seu menu de site preferido).
- Selecione o botão `Novo` na Barra de Ferramentas.
- Preencha o formulário Editar Item de Menus
  - Título: Animais
  - Alias: criaturas - já existe um item de menu chamado Animais, então você deve usar um alias diferente.
  - Tipo de Item de Menu: Alias do Item de Menu
  - Item de Menu: Animais - selecionado na lista de itens de menu existentes.

![submenus animais alias](../../../en/images/menus/submenus-animals-alias.png)

- Salvar
- Ordenação - após salvar, a ordem pode ser alterada. Neste exemplo, ele é colocado primeiro.

## Verifique o Resultado

Veja as páginas em seu site. Neste exemplo, a maioria das páginas não mostrará
os submenus na posição do lado esquerdo. O link Animais no menu superior
abrirá a página de animais a partir da qual é possível navegar para as
páginas de Gatos ou Cachorros:

![objetivos dos submenus animais cachorros](../../../en/images/menus/submenus-objectives-animals-dogs.png)

*Traduzido por openai.com*

