<!-- Filename: J4.x:Adding_a_New_Menu / Display title: Adição de um novo menu -->

Joomla!  4.x <span id="main-portal-heading">**Tutorial**
Como adicionar um novo menu</span>

## Introdução

Para que o conteúdo seja acessado em seu Joomla! os itens do site
precisam ser atribuídos a um menu. Uma instalação padrão do Joomla! cria
um **menu principal** para você. Em muitos casos, você usará apenas um
menu, mas poderá ter mais de um. Isso permite que você crie menus para
diferentes tipos de conteúdo, conteúdo oculto, conteúdo específico para
as funções dos usuários e muito mais.

Neste tutorial, você encontrará um passo a passo completo dos passos
envolvidos na criação de um menu em um site Joomla!. Vamos configurar um
novo menu, criar um módulo para menu, posicioná-lo em um local definido
no tema do site e adicionar itens dos menus a ele.

## Criar um novo menu

Abra uma nova janela do navegador e insira a URL, que será semelhante a
`http://www.nome-do-seu-site-aqui.com/administrator` ou, se você tem o
Joomla! instalado em seu computador local,
`http://localhost/nome-da-sua-pasta-aqui/administrator`. Aqui você terá
que iniciar a sessão como administrador ou super administrador.

Existem 2 maneiras de acessar o gerenciador dos menus que é usado para
adicionar um menu:

- A partir do painel inicial, no menu da barra lateral, acione o (clique
  no) ícone do painel do menu para ser levado ao gerenciador dos menus e
  acione (clique em) **Gerenciar**.
- Ou, a partir do painel inicial, no menu da barra lateral, expanda a
  seção **Menus** e acione (clique em) **Gerenciar**.

<img
src="https://docs.joomla.org/images/thumb/a/aa/J4.x_menus_dashboard_link-en.png/400px-J4.x_menus_dashboard_link-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/aa/J4.x_menus_dashboard_link-en.png 1.5x"
data-file-width="562" data-file-height="263" width="400" height="187"
alt="J4.x menus dashboard link-en.png" />

Quando o gerenciador dos menus abrir, ele mostrará os menus atuais e uma
barra de ferramentas superior com um botão **+ Novo**. Acione o (clique
no) botão "+ Novo".

<img
src="https://docs.joomla.org/images/thumb/3/3e/J4.x_menus_dashboard_links-en.png/800px-J4.x_menus_dashboard_links-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/3/3e/J4.x_menus_dashboard_links-en.png 1.5x"
data-file-width="1000" data-file-height="356" width="800" height="285"
alt="J4.x menus dashboard links-en.png" />

Agora um **título** e um **nome exclusivo** são necessários. Uma
**descrição** é opcional:

<img
src="https://docs.joomla.org/images/thumb/c/c2/J4.x_menu_manager_new-en.png/800px-J4.x_menu_manager_new-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/c/c2/J4.x_menu_manager_new-en.png 1.5x"
data-file-width="1000" data-file-height="422" width="800" height="338"
alt="J4.x menu manager new-en.png" />

**Título**: Um título adequado para o menu. Isso é usado para
identificar o menu no gerenciador dos menus.

**Nome único**: Este deve ser um nome de identificação exclusivo usado
pelo Joomla! para identificar este menu. Espaços não são permitidos mas
você pode usar o caractere "-" como, por exemplo, "menu-de-recursos".

**Descrição**: Embora não seja obrigatória, uma descrição do menu pode
ser útil para sua própria referência ou de outros administradores do
site.

Acione o (clique no) botão **Salvar** ou **Salvar e fechar** na barra
das ferramentas para criar o novo menu. O botão **Salvar e fechar** o
levará de volta ao gerenciador dos menus. Se você estava criando mais de
um menu, você também tem a opção de acionar (clicar em) **Salvar e
novo**. Para sair sem salvar o menu, acione o (clique no) botão
**Cancelar** na barra das ferramentas.

Se você escolher **Salvar e fechar**, você verá seu novo menu na lista
dos menus.

Neste ponto, você poderá começar a adicionar itens ao seu novo menu. No
entanto, vamos criar um módulo que mostrairá seu menu e podemos fazer
isso a partir do gerenciador dos menus.

## Criar o módulo para o seu menu

Click the **Add a module for this menu** button.

<img
src="https://docs.joomla.org/images/thumb/d/d1/J4.x_menu_manager_add_module-en.png/800px-J4.x_menu_manager_add_module-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/d/d1/J4.x_menu_manager_add_module-en.png 1.5x"
data-file-width="1000" data-file-height="206" width="800" height="165"
alt="J4.x menu manager add module-en.png" />

Um **módulo para menus** será aberto pronto para a entrada das
informações necessárias. Aqui estão alguns dos pontos mais básicos sobre
os módulos para menus:

O campo **Título** é obrigatório, então crie um título descritivo. Se
você deseja que este título seja mostrado na frente do site, acione o
(clique no) botão "Mostrar título", à direita. Observe o campo
**Selecionar menu**. Isso deve mostrar o nome do menu que você acabou de
criar. Você precisa selecionar uma **posição** em seu tema para onde
deseja que seu menu apareça. Nota: fazer com que fique do jeito que você
quer depende do estilo do seu tema. Selecione a posição desejada.

<img
src="https://docs.joomla.org/images/thumb/a/a1/J4.x_create_menu_module-en.png/800px-J4.x_create_menu_module-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/a1/J4.x_create_menu_module-en.png 1.5x"
data-file-width="1000" data-file-height="524" width="800" height="419"
alt="J4.x create menu module-en.png" />

Há muitas opções para escolher nos módulos para menus, como datas
relacionadas às publicações, acessos dos usuários e itens que serão
submenus, apenas para citar alguns. Para informações detalhadas sobre os
módulo para menus e todos os seus parâmetros consulte:  Módulo para
menus.

Depois que as informações forem adicionadas, acione (clique em) **Salvar
e fechar** e você retornará ao gerenciador dos menus.

## Adicionar itens ao seu menu

Para criar os links em seu menu, você precisa adicionar **itens dos
menus**. Existem muitos tipos de tipos de itens dos menus no Joomla!.
Alguns estão incluídos na instalação principal e muitos componentes de
terceiros também podem adicionar mais tipos. Para este tutorial,
adicionaremos links para artigos únicos.

A lista do gerenciador dos menus agora incluirá o novo menu. Na coluna
**Itens dos menus**, acione o (clique no) ícone.

<img
src="https://docs.joomla.org/images/thumb/3/31/J4.x_menu_manager_new_menu_item-en.png/800px-J4.x_menu_manager_new_menu_item-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/3/31/J4.x_menu_manager_new_menu_item-en.png 1.5x"
data-file-width="1000" data-file-height="168" width="800" height="134"
alt="J4.x menu manager new menu item-en.png" />

Para começar, isso apresentará uma lista vazia. Acione o (clique no)
botão **Novo** na barra das ferramentas.

<img
src="https://docs.joomla.org/images/thumb/a/af/J4.x_menu_manager_new_menu_item_2-en.png/800px-J4.x_menu_manager_new_menu_item_2-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/af/J4.x_menu_manager_new_menu_item_2-en.png 1.5x"
data-file-width="1000" data-file-height="267" width="800" height="214"
alt="J4.x menu manager new menu item 2-en.png" />

O painel **Menus: Novo item** será aberto. Adicionaremos um único artigo
ao menu:

- No campo **Título** adicione o título que deseja que apareça no menu.
- No campo **Tipo do item dos menus** acione o (clique no) botão
  **Selecionar** e depois acione (clique em) **Artigo** e **Artigo
  único**.
- No campo **Selecionar artigo** acione o (clique no) botão
  **Selecionar** que abrirá uma lista contendo os seus artigos.
  Selecione seu artigo.
- Verifique se o campo **Menu** está definido como novo menu.
- O campo **Estado** deve ser definido como **Publicado**.
- Acione (clique em) **Salvar e fechar**.

<img
src="https://docs.joomla.org/images/thumb/a/a4/J4.x_menu_manager_new_menu_item_3-en.png/800px-J4.x_menu_manager_new_menu_item_3-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/a4/J4.x_menu_manager_new_menu_item_3-en.png 1.5x"
data-file-width="1000" data-file-height="425" width="800" height="340"
alt="J4.x menu manager new menu item 3-en.png" />

Adicione mais itens dos menus ao novo menu.

Uma vez que os itens tenham sido adicionados ao menu, podemos verificar
se o menu é mostrado no site na posição correta.

Para recapitular, criamos um novo menu, depois um módulo para menus para
mostrar o menu no site e, finalmente, adicionamos alguns links de
artigos únicos ao novo menu. Verificando o site, podemos ver que o menu
é mostrado na posição que escolhemos e mostra os links de artigos únicos
adicionados ao menu.

<img
src="https://docs.joomla.org/images/thumb/5/51/J4.x_menu_sidebar_position-en.png/800px-J4.x_menu_sidebar_position-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/5/51/J4.x_menu_sidebar_position-en.png 1.5x"
data-file-width="1000" data-file-height="256" width="800" height="205"
alt="J4.x menu sidebar position-en.png" />
