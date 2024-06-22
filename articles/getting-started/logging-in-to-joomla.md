<!-- Filename: J4.x:Logging_in_to_Joomla / Display title: Iniciando sessão no Joomla -->

<span id="main-portal-heading">**Tutorial**  
Entrando e saindo do Joomla!</span> Joomla!  4.0

## Introdução

Uma das grandes coisas sobre o Joomla! é que ele oferece a flexibilidade
de realizar tarefas através do painel do administrador (geralmente
chamado de back-end) e, se ativado, realizar tarefas diretamente da
parte front-end (o público) do site.

O acesso front-end é uma maneira fácil e eficiente de permitir que os
criadores de conteúdo adicionem ou editem artigos rapidamente sem a
necessidade de acessar o painel do administrador.

Seu início de sessão no Joomla é configurado para controlar o que você
pode ver e fazer (ou não) usando o gerenciador de usuários do Joomla e
os poderosos níveis de controle de acesso (ACL). Isso significa que um
site Joomla pode ter usuários que usam apenas o backend, alguns que usam
apenas o frontend e outros que usam ambos.

As orientações a seguir cobrem o início e o término de sessão no backend
e no frontend em seu site Joomla.

**Nota:** Seu administrador do Joomla pode ter desabilitado o acesso
frontend, exigindo que todas as tarefas sejam realizadas usando o painel
do administrador backend.

Os passos cobertos neste tutorial são baseados em uma instalação padrão
do Joomla!.

## Entrar e sair do painel do administrador back-end

### Iniciando sessão

Navegue até a página de início de sessão do administrador. Este é o
endereço web do seu site anexado com /administrator, por exemplo,
meu-website-joomla.com/administrator

Isso levará você ao início de sessão do administrador no Joomla:

<img
src="https://docs.joomla.org/images/thumb/2/2a/J4x_administrator_login_en.png/800px-J4x_administrator_login_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/2/2a/J4x_administrator_login_en.png 1.5x"
data-file-width="1000" data-file-height="562" width="800" height="450"
alt="J4x administrator login en.png" />

1.  Adicione seu **nome de usuário**;
2.  adicione sua **senha**.

Clique no botão para **iniciar sessão** e você será levado para o painel
inicial do Joomla!.

**Notas:**

1.  O Joomla oferece a opção de configurar e usar a autenticação web -
    isso não está dentro do escopo deste tutorial;
2.  se o site tiver outros idiomas instalados, você poderá selecionar o
    idioma relevante a partir de uma lista suspensa antes de iniciar a
    sessão.

### Terminando sessão

Para terminar a sessão clique no **menu do usuário** e depois em
**término de sessão**.

<img
src="https://docs.joomla.org/images/thumb/8/89/J4x_administrator_logout_en.png/800px-J4x_administrator_logout_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/8/89/J4x_administrator_logout_en.png 1.5x"
data-file-width="1000" data-file-height="159" width="800" height="127"
alt="J4x administrator logout en.png" />

## Entrar e sair no frontend do site

### Entrando

Se o acesso frontend estiver ativado, um formulário de início de sessão
será adicionado ao site. O Joomla permite várias maneiras de fazer isso.
Uma instalação padrão inclui um formulário de início de sessão na barra
lateral do site, mas você pode descobrir que um link foi adicionado ao
menu do site, ou talvez no rodapé. Em alguns casos pode existir um link
*criar página*. O design do site ditará onde você acessa o formulário de
início de sessão.

Neste exemplo, usamos um formulário de início de sessão no site que está
localizado na barra lateral.

<img
src="https://docs.joomla.org/images/thumb/a/ae/J4x_front_end_login_en.png/800px-J4x_front_end_login_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/ae/J4x_front_end_login_en.png 1.5x"
data-file-width="1000" data-file-height="548" width="800" height="438"
alt="J4x front end login en.png" />
  
No **formulário de início de sessão**:

1.  Adicione seu **nome de usuário**;
2.  adicione sua **senha**.

Clique no botão **iniciar sessão**.

Ao iniciar sessão a partir do frontend do site, você será mantido na
mesma página em que iniciou a sessão. Você notará que o formulário de
início de sessão também será substituído por um botão para **terminar
sessão**.

### Terminando sessão

<img
src="https://docs.joomla.org/images/thumb/a/a9/J4x_front_end_logout_en.png/800px-J4x_front_end_logout_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/a9/J4x_front_end_logout_en.png 1.5x"
data-file-width="1000" data-file-height="233" width="800" height="186"
alt="J4x front end logout en.png" />

Para terminar a sessão, vá para a posição em que você se conectou e
clique no botão para **terminar sessão**.

## Dicas rápidas

- Alguns administradores de sites Joomla instalam extensões que ocultam
  ou restringem o acesso ao painel do administrador backend. Talvez seja
  necessário executar passos adicionais ou visitar um url de início de
  sessão alternativo;
- se você estiver fazendo edições usando o formulário de início de
  sessão frontend, economize tempo iniciando sessão na página que deseja
  editar.
