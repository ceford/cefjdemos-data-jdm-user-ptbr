<!-- Filename: Changing_user_groups / Display title: Alterando Grupos do Usuário  -->

## Herança de Grupos

Listas de grupos utilizam um padrão de herança. Por exemplo, um usuário no grupo Autor herda todos os privilégios do grupo Registrado e ganha alguns privilégios extras. Da mesma forma, um usuário no grupo Editor herda todos os privilégios do grupo Autor e ganha ainda mais privilégios extras. Os grupos de backend herdam o nível de privilégio mais alto no frontend.

Por esse motivo, você só precisa selecionar um grupo para um usuário individual - o grupo com mais privilégios.

## Etapas

Você pode alterar o grupo de um usuário seguindo estas etapas. Você deve fazer login como Administrador ou Superusuário para poder alterar os grupos de um usuário. Além disso, um Administrador não pode tornar a si mesmo ou a outros um Superusuário.

1. No *Painel Inicial* selecione o item **Usuários**. Ou...
2. No item de menu *Usuário* selecione **Usuários** e depois **Gerenciar**.
3. Encontre o usuário necessário na lista de usuários. Você pode pesquisar por nome, nome de usuário, email ou id: prefixo.
4. Selecione o nome do usuário para editar.
5. Selecione a aba *Grupos de Usuários Atribuídos*.
6. Selecione a qual grupo o usuário precisa pertencer.
7. Selecione *Salvar*.

## Lista de Controle de Acesso (ACL) para Joomla

A seguir, estão listadas as Listas de Controle de Acesso (ACL) para Joomla. O grupo de usuários é listado, e os marcadores abaixo descrevem as permissões associadas a esse grupo.

### Grupos de Frontend

#### Visitante

- Visualizar site público e artigos públicos

#### Registrado

- Privilégios do Grupo Visitante
- Visualizar artigos registrados
- Sem acesso a itens restritos ao Grupo Visitante

#### Autor

- Privilégios do Grupo Registrado
- Criar novos artigos
- Editar artigos que possuem
- Visualizar conteúdo especial

#### Editor

- Privilégios do Grupo Autor
- Editar todos os artigos, incluindo os não publicados

#### Publicador

- Privilégios do Grupo Editor
- Publicar artigos

### Grupos de Backend

Esses grupos permitem que você faça login no Administrador através do URL */administrator*.

#### Gerente

- Privilégios do Grupo Publicador
- Acesso ao Backend do Administrador

#### Administrador

- Privilégios do Grupo Gerente
- Criar novos usuários
- Instalar extensões

#### Superusuário

- Privilégios de Administrador
- Alterar o modelo do site
- Alterar a configuração global

*Traduzido por openai.com*

