<!-- Filename: J4.x:Adding_a_New_Menu / Display title: Adicionando um Novo Menu   -->

## Introdução

Para que o conteúdo seja acessado em seu site Joomla!, os itens precisam ser atribuídos a um Menu. Uma instalação padrão do Joomla! cria um **Menu Principal** para você. Em muitos casos, você usará apenas um menu, mas é possível ter mais de um. Isso permite criar Menus para diferentes tipos de conteúdo, conteúdo oculto, conteúdo específico para papéis de usuário, e mais.

Existem três etapas na criação de um menu utilizável:

1. Criar o Menu. Este é um contêiner para Itens de Menu.
2. Criar um Módulo de Menu. Isso permite a colocação do Menu em uma página.
3. Criar Itens de Menu. Estes são os itens selecionáveis que levam a páginas específicas.

Esta captura de tela mostra os menus disponíveis em um site multilíngue. Em uma instalação inicial do Joomla, existe um único *Menu Principal*.

![Lista de Menus](../../../en/images/menus/menus-manage.png "Lista de Menus")

A lista permite que você selecione qualquer um dos botões verdes ou vermelhos para ir diretamente à lista de itens de menu naquele menu e estado.

Este tutorial aborda as etapas envolvidas na criação de um Menu em um site Joomla!.

## Criar um Novo Menu

Use um dos seguintes passos para criar um novo menu:

- No menu do Administrador, selecione o *Ícone do Dashboard de Menu* para ser levado ao dashboard de Menu, e em seguida selecione **Gerenciar**. Ou...
- No Menu do Administrador expanda a seção *Menus* e depois selecione **Gerenciar**.
- Selecione o botão **+ Novo** na Barra de Ferramentas.
- No formulário de entrada de dados do Menu, complete os seguintes campos:
  - **Título**: Um título apropriado para o menu. Este é usado para identificar o menu no Gerenciador de Menus.
  - **Nome Único**: Este deve ser um nome de identificação único usado pelo Joomla! para identificar este menu. Espaços não são permitidos, mas você pode usar o caractere '-' como em recursos-menu.
  - **Descrição**: Embora não seja obrigatória, esta é frequentemente útil em um site com muitos menus. Ela aparece abaixo do *Título* na lista de menus como ilustrado acima.<br>
    ![Novo Menu](../../../en/images/menus/menus-new.png "Novo Menu")
- **Salvar & Fechar**

Na lista de Menus, o menu recém-criado possui um botão rotulado **Adicionar um módulo para este menu**, que é a próxima etapa na criação do menu. Você pode começar a adicionar itens de menu e voltar para criar o módulo do menu mais tarde.

## Criar um Módulo para o Menu

Na lista de Menus, a coluna *Módulos Vinculados* permite a seleção de qualquer módulo de menu existente para fins de edição. Você pode dar uma olhada e depois clicar em *Fechar* sem fazer nenhuma alteração. Para o seu novo menu, selecione o botão **Adicionar um módulo para este menu** para abrir uma moldura modal contendo o formulário de entrada de dados do módulo de Menu.

![Formulário de entrada de dados do módulo de Menu](../../../en/images/menus/menus-module.png "Formulário de entrada de dados do módulo de Menu")

Campos a serem preenchidos:

* O campo **Título** é obrigatório, então crie um título descritivo.
* O botão **Mostrar Título** à direita é usado para *Mostrar* ou *Ocultar* o título do módulo, um recurso comum a todos os módulos.
* O campo **Selecionar Menu** deve mostrar o nome do Menu que você acabou de criar.
* O campo **Posição** é usado para selecionar uma posição no seu template onde você deseja que seu menu apareça.
* Selecione **Salvar e Fechar** assim que as informações essenciais forem adicionadas.

Há muitas opções para escolher no formulário *Configurações de edição do módulo*. Elas são mencionadas na tela de Ajuda disponível no formulário *Módulo: Editar*. Este é o mesmo formulário, mas em uma página normal em vez de uma moldura modal. Acesse-o através do menu do Administrador, rota Conteúdo / Módulos do Site para a lista de Módulos do Site.

Nota: Fazer com que o Menu tenha a aparência que você deseja depende do estilo do seu template.

## Adicionar Itens ao Menu

Para criar os links em seu menu, você precisa adicionar **Itens de Menu**. Existem muitos *Tipos de Itens de Menu* no Joomla, e componentes de terceiros podem adicionar mais tipos. Para este tutorial, será adicionado um link para um único artigo.

Você pode criar um artigo com antecedência ou durante o processo de criação do menu. De qualquer forma, o artigo deve existir antes que um item de menu possa ser criado para ele. Neste exemplo, o artigo também será nomeado *Recursos*. Ele deverá conter uma lista de links para arquivos PDF.

Na lista de **Menus**, na coluna **Itens de Menu**, selecione o ícone para o menu recém-criado, *Recursos* neste exemplo. Inicialmente, não há itens de menu, então a lista apenas diz *Sem Resultados Correspondentes*.

- Selecione o botão **Novo** na Barra de Ferramentas para criar um novo item de menu.
- No campo **Título**, adicione o título que você deseja que apareça no Menu.
- No campo **Tipo de Item de Menu**, selecione o botão **Selecionar** para abrir um diálogo modal contendo uma lista de componentes. Cada um tem uma lista suspensa revelando uma lista de tipos de itens de menu disponíveis.
  - Selecione **Artigos** e depois **Artigo Único**.
- No campo **Selecionar Artigo**: **Ou:**
  - Use o botão **Selecionar** para selecionar um artigo existente. Ele abrirá uma lista de artigos para escolher. **Ou:**
  - Use o botão **Criar** para criar um novo artigo. Tudo o que você precisa fazer é inserir o título do artigo. Provavelmente é melhor deixar o conteúdo detalhado para depois.
- Verifique se o campo **Menu** está definido para o novo Menu.
- O campo **Status** deve estar definido como **Publicado**.
- Selecione **Salvar & Fechar**.

![Formulário de entrada de dados do item de menu](../../../en/images/menus/menus-single-article.png "Formulário de entrada de dados do item de menu")

Adicione mais Itens de Menu ao novo Menu conforme necessário.

Depois que os itens forem adicionados ao Menu, verifique se o Menu é exibido no site na posição correta.

![Exibição do menu](../../../en/images/menus/menus-display.png "Exibição do menu")

*Traduzido por openai.com*

