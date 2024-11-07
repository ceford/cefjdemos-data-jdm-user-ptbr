<!-- Filename: J4.x:User_Registration / Display title: Registro de Usuário -->

## Política de Registro

Em um site Joomla, usuários registrados têm permissão para fazer login e visualizar conteúdos ou interagir com conteúdos que usuários não registrados não podem acessar. O login no site e o login do Administrador são tratados separadamente, embora haja uma configuração Global que permite combiná-los. Alguns sites têm um pequeno número de usuários criados por um Administrador. Outros sites têm tantos usuários que é necessário que se auto-registrem e auto-ativem suas contas. A maneira como os usuários se registram no seu site é configurada no formulário *Usuários: Opções*.  

## Permitir Auto Registro

O auto registro de usuários é desativado por padrão. Qualquer novo usuário deve ser criado por um Gerente ou Administrador. O auto registro pode ser permitido com algumas mudanças simples no formulário *Usuários: Opções*.

- Selecione **Usuários → Gerenciar** no menu do Administrador.
- Selecione o botão *Opções* na Barra de Ferramentas.
- Defina **Permitir Registro de Usuário** para **Sim**.
- O **Grupo de Registro de Novo Usuário** deve ser **- Registrado -** a menos que haja uma razão válida para que seja algo diferente.
- A **Ativação de Conta de Novo Usuário** deve ser **Auto** ou **Administrador**.
  - Auto: O usuário receberá um e-mail com um link de ativação. A conta será ativada quando o usuário clicar no link de ativação.
  - Administrador: O usuário receberá um e-mail com um link de ativação. Quando o usuário clicar nesse link, o Administrador do Site será notificado por e-mail. Em seguida, o Administrador do Site precisará ativar a conta do usuário.

![Guia de opções de usuário de configuração de usuário](../../../en/images/users/users-configuration-user-options.png)

- **Salvar & Fechar**
- Adicione um módulo de *Login*. Ou
- Adicione um item de menu *Usuários: Formulário de Login* e um item de menu *Usuários: Logout*.

## Proibir Auto-Registro

- Defina **Permitir Registro de Usuário** como **Não**.

## Adicionando um Novo Usuário

Se o auto-registro não for permitido, qualquer novo usuário deve ser criado por um Administrador. Proceda da seguinte forma:

- Selecione o ícone **Usuários +** no painel do Dashboard Inicial. Ou
- Selecione **Usuários** → **Gerenciar +** no menu do Administrador.
- Preencha o formulário **Detalhes do Novo Usuário**. A maioria dos campos possui valores padrão adequados.

![Página de entrada de dados do novo usuário](../../../en/images/users/users-new-user.png)

- Selecione a aba **Grupos de Usuários Atribuídos** e marque a caixa correspondente ao grupo de usuários desejado. O grupo "Registrado" está marcado por padrão.
- **Salvar e Fechar**.
- Na lista de Usuários, verifique se a nova conta de usuário está Habilitada (visto verde nas colunas Habilitadas).

## Bloquear um Usuário

O melhor método para lidar com um usuário problemático é desativar a conta do usuário em vez de excluí-la. Essa medida pode ser utilizada para suspender o usuário e pode ser revertida se o usuário prometer se comportar. Excluir uma conta quebraria qualquer vínculo com conteúdos contribuídos pelo usuário, como autoria de artigos, e poderia permitir que o usuário se registrasse novamente com o mesmo endereço de e-mail.

Para bloquear um usuário:

- Selecione **Usuários → Gerenciar** no menu do Administrador.
- Encontre o usuário na lista de *Usuários*. Use o filtro de texto, se necessário.
- Selecione o ícone Habilitado que aparece como um tique verde ao lado do nome do usuário. Uma etiqueta **Bloquear** aparecerá ao passar o mouse.

![Página de inserção de dados de novo usuário](../../../en/images/users/users-hover-block.png)

- Selecione o ícone *Habilitado*. A página será recarregada com o ícone Habilitado aparecendo como uma cruz cinza.

## Desbloqueando um Usuário

Simples:

- Alterne o ícone *Ativado* de volta para um sinal verde.

*Traduzido por openai.com*

