<!-- Filename: Enabling_the_Login_Form_module / Display title: Formulário de Login   -->

## Métodos de Login no Site

Existem duas maneiras de permitir que usuários registrados façam login no frontend de um site. Há um item de menu **Formulário de Login** que pode ser encontrado no grupo de itens do menu Usuários. As permissões de *Acesso* dele precisam ser configuradas para *Convidado*. Um segundo item de menu *Logout* é necessário com suas permissões de *Acesso* configuradas para *Registrado*.

A alternativa é o módulo **Formulário de Login**. Ele é instalado por padrão na posição *sidebar-right* em uma nova instalação do Joomla. Este módulo pode ser movido para outra posição, despublicado, enviado para a lixeira e excluído. As ações mencionadas se aplicam a uma instância do módulo e não ao código do módulo. Portanto, você pode criar um novo módulo *Formulário de Login* ou fazer uma duplicata, talvez para uso em diferentes templates. O módulo Formulário de Login altera sua exibição após o login para apresentar um botão *Logout*.  

## O Módulo de Formulário de Login

Para publicar um Formulário de Login não publicado:

* Selecione **Conteúdo → Módulos do Site** no menu do Administrador.
* Localize o módulo **Formulário de Login**.
* Se o ícone de **Status** for um tique verde dentro de um círculo, ele já está ativado. Se o ícone de Status for um "x" cinza, ele está atualmente desativado. Selecione o ícone para habilitar o módulo.
* Se o módulo *Formulário de Login* não estiver presente na lista, ajuste as Opções de Filtro, selecione o campo - *Selecione Status* - para *Todos* ou *Lixeira* para verificar se foi movido para a lixeira. Se sim, ele pode ser publicado selecionando seu ícone de lixeira.
* Caso o módulo Formulário de Login esteja ausente, crie um novo.

Para criar um novo Formulário de Login ou um segundo Formulário de Login:

* Selecione **Conteúdo → Módulos do Site** no menu do Administrador.
* Selecione o botão **Novo** na Barra de Ferramentas.
* Na lista de Módulos, selecione o item **Login**.
* Preencha o formulário de entrada de dados *Módulos: Login*.
  - Insira um Título único.
  - Selecione uma posição de template ou crie uma posição nomeada para uso em um artigo.
  - Preencha outros campos conforme apropriado.
* **Salvar & Fechar**
* Teste o módulo para garantir que aparece corretamente no frontend do site.

## Para atribuir o módulo Formulário de Login a páginas da web selecionadas

Você pode fazer com que o módulo Formulário de Login apareça em uma ou mais páginas ao atribuí-lo a Itens de Menu selecionados. Isso é feito usando os campos no grupo Atribuição de Menu na tela de Edição do Módulo:

- Selecione a aba **Atribuição de Menu**.
- A lista **Atribuição de Módulo** possui quatro opções:
  - **Em todas as páginas**: O módulo Formulário de Login aparecerá em todas as páginas.
  - **Em nenhuma página**: O módulo Formulário de Login não aparecerá em nenhuma página.
  - **Somente nas páginas selecionadas**: Uma lista de todos os menus e itens de menu do seu site aparecerá. O módulo Formulário de Login aparecerá nas páginas selecionadas nesta lista.
  - **Em todas as páginas, exceto as selecionadas**: O formulário de login aparecerá em todas as páginas não selecionadas.
- **Seleção de Menu**: Mostra uma lista de todos os Menus e Itens de Menu dos quais um ou mais podem ser selecionados. Este campo é usado apenas se o campo **Menus** estiver definido como **Selecionar Item(ns) de Menu da Lista**.

  ![atribuição de menu do módulo](../../../en/images/modules/modules-login-menu-assignment.png)

## Para personalizar o módulo de Formulário de Login

Se você deseja alterar a aparência do módulo de Login, pode adicionar estilos, sejam eles estilos do Bootstrap ou seus próprios estilos definidos no arquivo user.css do seu template. Adicione os estilos na aba **Avançado** do formulário de edição de Módulos: Login.

Se você deseja alterar as informações exibidas no formulário de Login, pode criar uma substituição de template. Consulte a seção sobre [Substituições de Template](jdocmanual?article=user/templates/template-overrides) para mais detalhes.

*Traduzido por openai.com*

