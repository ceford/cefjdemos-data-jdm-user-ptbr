<!-- Filename: J4.x:Login_and_Logout_Redirects / Display title: Redirecionamentos de Login e Logout -->

## Padrões

Login e Logout têm opções para selecionar uma página para a qual redirecionar após o sucesso. Existem padrões, mas eles podem não ser apropriados para o seu site. Por exemplo, o formulário de Login leva à página de Perfil do Usuário por padrão. Isso se torna tedioso se não houver uma boa razão para ver a página de Perfil em cada login.

Este artigo aborda as opções de redirecionamento disponíveis após um login ou Logout bem-sucedidos.

## Módulo de Login

O comportamento padrão de um módulo de login é permanecer na mesma página após o login e logout. O único problema com esse comportamento é que um usuário que fizer logout de uma página restrita será solicitado a fazer login novamente. Se isso for problemático, uma solução fácil é selecionar a página inicial para redirecionar no campo de configurações do Módulo, Página de Redirecionamento de Logout.

![formulário de menu de logout restrito para acesso registrado](../../../en/images/users/login-redirects-login-form.png)

Dica: Você pode usar dois módulos de login. Um com acesso **Convidado** intitulado **Login**. O segundo com acesso **Registrado** intitulado **Logout**.

## Item de Menu de Login

O tipo de item de menu de login pode ser usado para login e logout. Se utilizado para ambos os propósitos, ele deve ter um título como Login/Logout. Se isso parecer estranho, você pode usar itens de menu separados para Login e Logout.

O tipo de item de menu de Login permite uma escolha do Tipo de Redirecionamento de Login: por Item de Menu ou por URL Interna. Por padrão, o Item de Menu é selecionado, mas não configurado, e o login leva à página de Perfil do Usuário. Você pode selecionar um item de menu ou fornecer a URL de uma página. Por exemplo, você poderia ter uma página de Status do Sistema com uma mensagem do dia personalizada.

![formulário de logout restrito a acesso registrado](../../../en/images/users/login-redirects-login-menu-options.png)

O comportamento padrão do Logout é redirecionar para a página Inicial do site. Você poderia redirecionar para outra coisa, como uma mensagem de Adeus vinculada por um item de menu ou uma URL interna.  

## Item de Menu de Logout

O item de menu de Logout é simples. O padrão é permanecer na mesma página após o logout. Se isso for inconveniente, selecione a página inicial do site.

![formulário de menu de logout restrito ao acesso registrado](../../../en/images/users/login-redirects-logout-menu-options.png)

*Traduzido por openai.com*

