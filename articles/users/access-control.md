<!-- Filename: J4.x:Access_Control / Display title: Controle de Acesso  -->

## Introdução

O Joomla possui um mecanismo sofisticado para controlar quem pode ver e manipular o conteúdo em um site Joomla. A parte do **quem** é configurada nas opções do componente Usuários com Grupos de Usuários e Níveis de Acesso. A parte de **manipular** é configurada nas Permissões de Ação, seja nas configurações globais, nas configurações de componentes ou nas configurações de itens. Por exemplo, os valores padrão configurados nas Permissões Globais podem ser substituídos nas Permissões de Artigos (todos os artigos) e as Permissões de Artigos podem ser substituídas nas Permissões de Artigos individuais.

## Grupos de Usuários

Os Grupos de Usuários são usados para dividir os usuários do site em grupos com diferentes responsabilidades. Por exemplo, membros do grupo de usuários Autor têm permissão para fazer login no site, criar artigos e editar seus próprios artigos. Nada mais! Membros do grupo Super Usuários têm responsabilidade por todos os aspectos da gestão e operação do site. O Joomla fornece nove grupos de usuários padrão e você pode criar mais, se necessário.

![Lista de grupos de usuários](../../../en/images/users/access-control-users-groups-list.png)

Os grupos de usuários padrão são configurados com relações de pai e filho para minimizar a duplicação de permissões. Exemplos de herança:

- Um membro do grupo Registrado não tem permissão para acesso como Administrador. Nem o Editor ou Publicador.
- Um membro do grupo Autor tem permissão para Criar e Editar Próprios Itens. O mesmo vale para o Editor e Publicador, mas eles têm permissões extras.

Você pode criar novos grupos de usuários para fins especiais conforme necessário. Por exemplo, você pode querer criar um grupo que tem permissão para fazer login como Administrador, mas com acesso restrito a um único componente. Há um exemplo de tal grupo de usuários personalizado no final deste tutorial.

## Níveis de Acesso

Cada vez que você cria um objeto, como um artigo, um módulo ou um item de menu, verá um campo de Acesso, geralmente na coluna direita do formulário de entrada de dados. É uma lista suspensa que oferece uma escolha entre Público, Visitante, Registrado, Especial e Super Usuários. O padrão é Público. Os níveis de acesso de visualização padrão são mostrados na captura de tela a seguir:

![Usuários visualizando níveis de acesso](../../../en/images/users/access-control-users-access-levels.png)

Exemplos:

- Se você criar um módulo do site e definir o Acesso como Registrado, ele será visto apenas por usuários que estiverem conectados ao site.
- Se você criar um item de menu do site e definir o Acesso como Super Usuários, ele será visto apenas por Super Usuários que estiverem conectados ao site.

## Permissões

As Permissões de Configuração Global são o ponto de partida a partir do qual as configurações de permissão em componentes ou itens individuais podem herdar ou substituir. Captura de tela:

![permissões de configuração global](../../../en/images/users/access-control-global-configuration-permissions.png)

A captura de tela mostra que os membros do grupo Público não têm permissão para realizar nenhuma ação. Se você selecionar cada grupo, verá como as permissões mudam de grupo para grupo. Note que o Gerente e o Administrador estão autorizados a realizar o Login de Administrador, mas o Autor, o Editor e o Publicador não estão. Estes últimos são efetivamente papéis do Site em vez de papéis de Administrador.

Todas as permissões dos grupos herdam do grupo Público. Ele não tem permissão para nenhuma ação. No entanto, por padrão, os itens no grupo Público podem ser visualizados, então atribuir permissão Pública a um item permitirá que ele seja visto por todos os visitantes do site, estejam eles logados ou não.

### Permissões de Artigos

As ações de Permissões de Artigos diferem das ações de Permissões de Configuração Global. Não estão presentes itens relacionados a login, mas estão presentes itens relacionados a fluxos de trabalho. Este é um padrão bastante típico: um componente terá permissões relevantes para o componente; um item de componente (como um artigo) terá permissões relevantes para aquele único item.

![Permissões de conteúdo](../../../en/images/users/access-control-global-content-permissions.png)

### Permissões de Artigo Único

As permissões de um artigo único têm apenas três itens: Excluir, Editar e Editar Estado:

![permissões de artigo único](../../../en/images/users/access-control-article-permissions.png)

## Exemplo de Controle de Acesso: Usuário de Propósito Especial

Suponha que você precise criar um Grupo de Usuários para usuários que têm apenas uma responsabilidade, neste exemplo, um Administrador de Artigos. Usuários deste grupo devem ter permissão para Login de Administrador, mas não devem ver nada além dos itens de Conteúdo. Procedimento:

### Criar um novo Grupo de Usuários

- Selecione **Usuários → Grupos** no menu do Administrador.
- Selecione o botão `Novo` na Barra de Ferramentas.
- Preencha o campo Título do Grupo: Administrador de Artigos
- O Grupo Pai deve ser Público - não tem permissões para nada.

![Formulário de novo grupo de usuários](../../../en/images/users/access-control-new-group.png)

### Atribuir a Especial 

- Selecione **Usuários → Níveis de Acesso** no menu do Administrador.
- Selecione o item **Especial**.
- Marque a caixa do Administrador de Artigos no formulário **Usuários: Editar Nível de Acesso de Visualização**.
- Salvar & Fechar.

![Selecionar acesso para grupo](../../../en/images/users/access-control-select-access-for-group.png)

### Permissões de Configuração Global

- Selecione **Painel Inicial → Configuração Global** no menu do Administrador.
- Selecione a aba **Permissões**.
- Selecione o grupo **Administrador de Artigos**.
- Defina **Login de Administrador** como Permitido.
- Salvar & Fechar

![Selecionar acesso para grupo](../../../en/images/users/access-control-article-administrator-global-permissions.png)

### Permissões de Opções de Artigos

- Selecione **Conteúdo → Artigos** no menu do Administrador.
- Selecione o botão `Opções` na Barra de Ferramentas.
- Selecione a aba **Permissões**.
- Selecione o grupo **Administrador de Artigos**.
- Configure todos os itens exceto os dois primeiros (Configurar ACL & Opções e Configurar somente Opções) como Permitido.
- Salvar & Fechar

![Selecionar acesso para grupo](../../../en/images/users/access-control-article-administrator-content-permissions.png)

### Criar ou Editar Usuário

- Crie um novo usuário ou edite um usuário existente que não esteja atribuído a nenhum grupo
- Selecione **Administrador de Artigos** na guia **Grupos de Usuários Atribuídos** do formulário de edição do Usuário.
- Salvar & Fechar.
- Faça login como um usuário apenas no Grupo Administrador de Artigos. O menu deve mostrar apenas itens relacionados a artigos:

![Selecionar acesso para grupo](../../../en/images/users/access-control-article-administrator-home-dashboard.png)

*Traduzido por openai.com*

