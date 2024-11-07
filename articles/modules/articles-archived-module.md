<!-- Filename: J4.x:How_to_Show_a_Calendar_Month_List_of_Archived_Articles_Using_a_Module / Display title: Artigos Arquivados  -->

## Introdução

Arquivar artigos é uma das maneiras que o Joomla! ajuda a gerenciar os artigos de um site, pois contribui para reduzir a desorganização no backend. Mas quais visitantes do site devem poder acessar os artigos arquivados?

Uma maneira de fazer isso é mostrar uma lista de meses de um calendário com os artigos arquivados usando um dos Módulos principais do Joomla. Neste exemplo, um **Módulo de Artigos Arquivados** será configurado para ser exibido na barra lateral do site.

## Criar o Módulo *Artigos - Arquivados*

Use um dos seguintes métodos:
* Selecione o item **Módulos** no Painel Inicial. Ou...
* Selecione **Conteúdo / Módulos do Site** no menu do Administrador.
* Selecione o item **Artigos Arquivados** na lista de Módulos (Site).

Isso irá criar o novo módulo e abrir o módulo para configuração.

## Configurando o Módulo

Para o uso padrão do módulo, há apenas algumas configurações:

- **Título** Insira um nome para o módulo.
- **\# de Meses** Defina o número de meses que você deseja exibir. Eles aparecerão como links no front-end. Defina usando as setas para cima/para baixo ou insira um número diretamente no campo.
- **Exibir/Ocultar Título** Escolha se deseja ou não mostrar o título alternando para *Exibir* ou *Ocultar*.
- **Posição** Defina uma posição onde você deseja exibir o módulo no front-end. As posições são ditadas pelo seu template. Este exemplo usa a posição *Sidebar Direita* do template Cassiopeia do Joomla.
- **Status** Por padrão, o status do módulo é **Publicado**. Outras opções são **Não Publicado** e **Lixeira**.
- **Início da Publicação** Você pode agendar o início da publicação do módulo.
- **Final da Publicação** Você pode agendar quando parar a publicação do módulo.
- **Acesso** Se você deseja controlar quem pode ver o módulo no front-end, pode escolher um nível de acesso.
- **Ordenação** Usado para controlar onde o módulo é exibido dentro da posição que você selecionou. Por exemplo, você pode ter vários módulos na barra lateral e querer que este esteja no topo ou na parte inferior – ou em algum lugar entre outros na barra lateral. Pode ser um pouco confuso no início, pois o campo mostra uma posição numerada e um nome de módulo. O nome pode ser de um módulo que não está publicado. O que lembrar é que o número mais baixo estará no topo e o número mais alto na parte inferior.
- **Nota** Pode ser útil usar o campo de nota se, por exemplo, você estiver usando o mesmo tipo de módulo em vários lugares.

### Aba de Atribuição de Menu

Por padrão, o módulo será publicado **Em todas as páginas**.

Alternativamente, você pode escolher através de uma lista suspensa **Nenhuma página**, **Apenas nas páginas selecionadas** ou **Em todas as páginas, exceto as selecionadas**. As duas últimas opções fornecem uma árvore de menus dos menus usados no site onde você pode selecionar/deselecionar páginas.

### Outras Configurações

A aba **Avançado** tem configurações relacionadas ao layout do módulo quando ele é exibido.

A aba **Permissões** permite controlar o que os grupos de usuários podem fazer com o módulo.

## Publicando o Módulo

Quando estiver pronto, selecione o botão **Salvar & Fechar**.

O módulo será publicado na barra lateral do site e exibirá uma lista de links ditada pelo número de meses para exibição configurado no módulo.

![Exemplo de Módulo de Artigos Arquivados](../../../en/images/modules/modules-archived-articles.png "Exemplo de Módulo de Artigos Arquivados")

## Dicas

Quanto mais artigos arquivados você tiver, maior será o número de links exibidos pelo módulo. Pode ser mais apropriado limitar o número de links usando categorias ou você pode usar múltiplos Módulos de Artigos Arquivados nomeados de acordo.

*Traduzido por openai.com*  

