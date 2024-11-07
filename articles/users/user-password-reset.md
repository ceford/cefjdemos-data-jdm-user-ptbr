<!-- Filename: J4.x:User_Password_Reset / Display title: Redefinição de Senha do Usuário -->

## Redefinição de Usuário

Se seus usuários têm permissão para login no site e um usuário não consegue se lembrar do Nome de Usuário ou Senha, é melhor exigir que o indivíduo redefina suas credenciais por conta própria usando os links no formulário de login:

![módulo de login do usuário do site](../../../en/images/users/user-site-login-module.png)

Em cada caso, selecionar um link leva a um formulário para inserir o endereço de e-mail associado à conta:

![formulário de redefinição de senha esquecida do site](../../../en/images/users/user-forgot-password-reset.png)

Todo o processo é realizado pelo usuário sem a necessidade de intervenção de um Administrador. Este é o formulário de verificação de senha perdida:

![formulário de confirmação de senha esquecida do site](../../../en/images/users/user-forgot-password-confirm.png)

E, finalmente, o usuário deve inserir uma nova senha:

![formulário de redefinição de senha esquecida do site](../../../en/images/users/user-forgot-password-complete.png)

## Redefinição de Administrador

Se houver apenas login de Administrador, uma redefinição de senha do usuário deve ser realizada por um Superusuário ou Administrador. Se for o único Superusuário que não sabe as credenciais de login, consulte o artigo separado sobre Recuperação de Senha do Administrador. Caso contrário:

- Selecione **Usuários → Gerenciar** no menu do Administrador ou selecione
  *Usuários* no painel do Site do Painel Inicial.
- Encontre o usuário que precisa de uma redefinição de senha.
- Selecione o **Nome** vinculado para abrir o formulário *Usuário: Editar*.
- Insira uma nova senha nos campos Senha e Repetir Senha.
- Defina o campo **Exigir Redefinição de Senha** como *Sim*.
- **Salvar & Fechar**

![formulário de edição de usuário de administradores](../../../en/images/users/users-edit-user-john-doe.png)

Você precisará então enviar um e-mail para o usuário com a nova senha provisória em texto simples. Após o login, o usuário será capaz de ver a página inicial do site, mas qualquer tentativa de navegar para outra página levará o usuário ao formulário de nova senha.

*Traduzido por openai.com*

