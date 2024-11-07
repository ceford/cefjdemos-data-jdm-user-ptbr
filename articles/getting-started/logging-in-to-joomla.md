<!-- Filename: J4.x:Logging_in_to_Joomla / Display title: Fazendo login no Joomla  -->

## Introdução

Uma das grandes vantagens do Joomla! é a flexibilidade que oferece para realizar tarefas através do Painel do Administrador (frequentemente chamado de backend) e, se ativado, executar tarefas diretamente a partir do frontend (a parte pública) do website.

O acesso pelo frontend é uma maneira fácil e eficiente de permitir que os redatores de conteúdo adicionem ou editem artigos rapidamente sem a necessidade de acessar o Painel do Administrador.

O login do Joomla é configurado para controlar o que os usuários podem ver e fazer (ou não podem) usando o componente de Usuário do Joomla e os poderosos Níveis de Controle de Acesso (ACL). Isso significa que um site Joomla pode ter usuários que usam apenas o backend, alguns que usam apenas o frontend e outros que usam ambos.

O texto a seguir cobre o login e logout tanto no backend quanto no frontend de um site Joomla.

**Nota:** Um Administrador do Joomla pode ter desativado o acesso pelo frontend, exigindo que todas as tarefas sejam realizadas usando o Painel do Administrador no backend.

### Login do Administrador

Acesse a página de Login do Administrador. Este é o endereço web do site acrescido de /administrator, por exemplo, my-joomla-website.com/administrator, que invoca a página de login do Administrador do Joomla:

![Formulário de login do administrador](../../../en/images/getting-started/logging-in-to-joomla-administrator-login-form.png)

1. Adicione seu **Nome de Usuário**
2. Adicione sua **Senha**

Selecione o botão **Entrar** para ser direcionado ao Painel Inicial do Joomla!.

**Nota:**

1. Joomla fornece uma opção para configurar e usar a Autenticação Web.
   Isso não está dentro do escopo deste tutorial.
2. Se um site tiver vários idiomas instalados, você poderá
   selecionar um idioma para usar a partir de uma lista suspensa antes de fazer login.

### Logout do Administrador

Para sair, selecione o **Menu do Usuário** e depois **Sair**.

![Link de logout do administrador](../../../en/images/getting-started/logging-in-to-joomla-logout-link.png)

### Login no Site

Se o acesso pelo frontend estiver ativado, um formulário de login terá sido adicionado ao site. O Joomla permite várias maneiras de fazer isso. Uma instalação padrão inclui um formulário de login na barra lateral do site, mas você pode encontrar um link adicionado ao menu do site, ou talvez no rodapé. Em alguns casos, pode existir um link *Criar Página*. O design do site determinará onde acessar o formulário de login.

Este exemplo usa um formulário de login localizado na barra lateral direita.

![Módulo de formulário de login do site](../../../en/images/getting-started/logging-in-to-joomla-site-login-form.png)

No **Formulário de Login**

1. Adicione seu **Nome de Usuário**
2. Adicione sua **Senha**

Selecione o botão **Entrar**.

Ao fazer login a partir do frontend do site, você pode ser mantido na mesma página de onde fez o login ou pode ser levado à sua página de Perfil. Você notará que o formulário de login também conterá um botão **Sair**.

### Logout do Site

![Módulo de formulário de logout do site](../../../en/images/getting-started/logging-in-to-joomla-site-logout-form.png)

Para sair, vá até o formulário de login e selecione o botão **Sair**.

## Dicas

- Alguns administradores de sites Joomla instalam extensões que ocultam ou restringem o acesso ao Painel de Administração do backend. Você pode precisar tomar medidas adicionais ou visitar uma URL de login alternativa.
- Se você estiver fazendo edições usando o login no frontend, economize tempo fazendo login na página que deseja editar.

*Traduzido por openai.com*

