<!-- Filename: J4.x:Adding_a_Custom_Administrator_Menu / Display title: Menu Personalizado do Administrador -->

## Introdução

Suponha que você tenha um usuário a quem deseja permitir que execute apenas uma tarefa em seu site. Considere o caso de uma organização que possui filiais em todo o mundo e a única tarefa que cada filial tem permissão para realizar é colocar locais em um mapa para exibição no site. O componente para essa tarefa é o Ffmap, mas isso não será abordado aqui, exceto pelos itens do menu do Administrador envolvidos.

Para realizar essa tarefa, você precisa criar um Grupo de Usuários personalizado, atribuir um usuário a esse grupo e criar um menu personalizado para uso por esse usuário.

## Criar um Grupo de Usuários

- Selecione **Usuário → Usuários → Grupos** no menu do Administrador.
- Selecione o botão **Novo** na Barra de Ferramentas.
  - Insira um **Título *para o Grupo,*** *Filial* neste caso.
  - Selecione **Público** como o grupo pai. Isso é importante – você não
    quer herdar permissões de outro grupo.
- Selecione **Salvar e Fechar** na Barra de Ferramentas.

## Configurar Permissões Globais para o Grupo

- Selecione **Configuração Global** no Painel Inicial.
- Selecione a aba **Permissões**.
- Selecione o item **Filial**.
- Defina **Login de Administrador** como **Permitido**.
- Selecione **Salvar e Fechar** na Barra de Ferramentas.

Neste ponto, qualquer usuário atribuído ao Grupo de Usuários da Filial poderá
fazer login na interface do Administrador e ver o Painel Inicial. Pode haver
módulos do painel visíveis porque seu nível de acesso foi definido como
Público, por exemplo: Usuários Conectados, Artigos Populares e Artigos Adicionados Recentemente. É melhor definir o acesso a esses módulos como Especial. Não haverá itens de menu visíveis para o usuário.

## Definir Permissão de Componente para o Grupo

Opção 1:

- Selecione o componente **Ffmap** no menu do Administrador.
- Selecione o botão **Opções** do FFmap na barra de ferramentas para abrir sua tela de configuração.

Ou:

- Selecione **Configuração Global** no Painel Inicial.
- Selecione Ffmap na lista de componentes.

Então:

- Selecione a aba **Permissões** e, em seguida, o item **Ramo**.
- Defina as opções Acessar Interface de Administração, Criar, Excluir, Editar, Editar Estado, Editar Próprio e Editar Valor de Campo Personalizado como **Permitido**.
- Selecione **Salvar e Fechar** na barra de ferramentas.

## Criar um novo menu de Administrador

- Selecione **Menu → Gerenciar** no menu do Administrador.
- Selecione **Administrador** na lista suspensa Site/Administrador.
- Selecione o botão **Novo** na Barra de Ferramentas.
- Insira um título para o menu, por exemplo, **Menu Filial** e um id único, por exemplo, **menu-filial**.
- Selecione **Salvar e Fechar** na Barra de Ferramentas.

## Criar um Módulo para o menu

Na lista de Menus, selecione o botão **Módulos Vinculados** no registro do Menu do Filial.

- Insira um Título para o módulo, por exemplo, **Menu do Filial**.
- Selecione o Menu para Exibir: **Menu do Filial**.
- Defina Verificar Menu como **Não**, caso contrário, aparecerão mensagens de aviso sobre funções do Administrador ausentes.
- Selecione a posição: **menu**.

## Criar um Contêiner de Menu de Componentes

- Na lista de Menus, selecione o ícone de Itens de Menu para o Menu da Filial. Isso
  abrirá a lista de itens, que está vazia neste estágio.
- Selecione o botão **Novo** na Barra de Ferramentas.
- Insira um título para o item de menu: **Componentes da Filial**.
- Selecione o Tipo de Item de Menu **Selecionar Botão**.
  - Na caixa de diálogo modal, role para baixo até o item **Links do Sistema** e
    expanda o painel.
  - Selecione o tipo de item **Contêiner de Menu de Componentes**.
- De volta ao formulário de configuração do menu, selecione **Ocultar Nenhum** para esconder todos
  os itens do menu Componentes (vermelho).
- Role para baixo até os itens Ffmap e clique nos botões Ocultar para
  alterá-los para Mostrar (verde).
- Selecione **Salvar e Fechar** na Barra de Ferramentas.

## Captura de Tela

![seleção de componente do menu administrador personalizado](../../../en/images/menus/menus-custom-administrator-menu.png)

## Resultado

Crie um usuário no Grupo da Filial para você mesmo testar. Faça login na interface do Administrador como esse usuário para ver o resultado:

![resultado do menu personalizado do administrador](../../../en/images/menus/menus-custom-administrator-menu-result.png)

## Notas

Se você adicionar outro componente posteriormente, ele será adicionado ao Contêiner do Menu de Componentes e ficará visível por padrão. Você precisará voltar ao item do menu Administrador e definir o novo conteúdo como Oculto.

Se o componente estiver configurado para incluir itens de menu em cada uma das visualizações de lista do Administrador, através da inclusão de arquivos default.xml, você poderá adicionar itens de menu diretamente ao menu personalizado e evitar o uso do Contêiner do Menu de Componentes.

O menu Componentes da Filial permanecerá como parte do menu do Administrador - duplicação inevitável!

*Traduzido por openai.com*

