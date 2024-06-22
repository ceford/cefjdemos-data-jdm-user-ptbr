<!-- Filename: J4.x:Adding_a_New_Article / Display title: Adicionando um novo artigo -->

Joomla!  4.0 <span id="main-portal-heading">**Tutorial**
Adicionando um novo artigo</span>

## Introdução

Este tutorial é parte de uma série sobre como trabalhar com artigos no
Joomla!.

Ele cobre os métodos para adicionar um novo artigo após o início de
sessão no painel do administrador e é baseado em uma instalação padrão
do Joomla usando o editor de conteúdo padrão.

Para mais informações sobre os diferentes editores disponíveis no
Joomla, leia:  Editores de
conteúdo.

Antes de começar, além do conteúdo, caso você os use, precisará saber
qual categoria e quais tags atribuirá ao artigo.

- Inicie uma sessão no painel inicial do administrador. Mais informações
  sobre isso aqui:  Entrar ou sair do painel do
  administrador.

## Introdução

### Diretamente do painel inicial

<img
src="https://docs.joomla.org/images/thumb/4/4e/J4x_add_article_at_home_dashboard-en.png/800px-J4x_add_article_at_home_dashboard-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/4/4e/J4x_add_article_at_home_dashboard-en.png 1.5x"
data-file-width="1000" data-file-height="254" width="800" height="203"
alt="J4x add article at home dashboard-en.png" />

Dependendo se seu painel inicial foi personalizado após a instalação,
você terá uma ou duas opções para gerar um novo artigo:

1.  No menu da barra lateral, clique no link **Conteúdo** e, no menu
    suspenso, clique no **símbolo de mais (+)** à direita do link
    **Artigos**.
2.  Se for exibido, no painel inicial do site, clique no **símbolo de
    mais (+)** à direita do ícone de **Artigos**.

### Através do gerenciador de artigos

<img
src="https://docs.joomla.org/images/thumb/2/24/J4x_home_dashboard_add_article_en.png/800px-J4x_home_dashboard_add_article_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/2/24/J4x_home_dashboard_add_article_en.png 1.5x"
data-file-width="1000" data-file-height="147" width="800" height="118"
alt="J4x home dashboard add article en.png" />

Qualquer uma dessas opções abrirá uma página: **Artigos: Novo** que está
pronta para entrada.

## Preparando o artigo

<img
src="https://docs.joomla.org/images/thumb/0/05/J4x_add_article_basic_en.png/800px-J4x_add_article_basic_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/0/05/J4x_add_article_basic_en.png 1.5x"
data-file-width="1000" data-file-height="341" width="800" height="273"
alt="J4x add article basic en.png" />

Quando um novo artigo é gerado, ele abrirá um painel com abas com a aba
**Conteúdo** selecionada. É possível salvar um novo artigo com apenas
duas informações obrigatórias:

1.  Digite um título no campo *Título*. Isso é usado sempre que o título
    do artigo é exibido. (**Necessário**) O campo *Alias* ao lado do
    campo de título não é um campo obrigatório pois, se for deixado em
    branco, o Joomla criará o alias quando o artigo for salvo. O alias é
    usado para se referir ao artigo e é importante para os [recursos de
    endereço amigável para os mecanismos de
    pesquisas](https://docs.joomla.org/Search_Engine_Friendly_URLs "Special:MyLanguage/Search Engine Friendly URLs").
    O alias também pode ser usado por outras funcionalidades do site,
    como plugins e módulos, para encontrar o artigo.
2.  Escolha uma **categoria**. Consulte **Configurações de artigo**
    abaixo para obter mais informações.
3.  Embora não seja estritamente necessário para adicionar e salvar um
    artigo, insira seu conteúdo usando o editor.

### Parâmetros de artigos

As outras guias acima do editor de conteúdo incluem várias opções ou
parâmetros para o artigo. **Você pode não ver todas as guias a seguir**,
pois o administrador do site pode ocultar algumas para ajudar a manter a
consistência do layout do artigo em todo o site. Você também pode ver
guias adicionais para *Campos personalizados* se eles tiverem sido
configurados.

1.  *Imagens e links* permite que você defina uma introdução e uma
    imagem em destaque e/ou links para aparecer em posições
    predefinidas. Isso pode ser usado se seu artigo for exibido em um
    blog de categoria.
2.  *Opções* permite que você especifique o layout do artigo e
    informações associadas, como título, categoria, tags, detalhes de
    publicação, etc. Isso normalmente é definido globalmente, mas pode
    ser específico do artigo por meio dessas opções.
3.  *Publicar* permite definir datas e horários de publicação para
    agendar a publicação de um artigo. Por padrão, quando um artigo é
    salvo, ele será publicado imediatamente. Você também pode definir os
    metadados do artigo.
4.  *Configurar tela de edição* permite mostrar ou ocultar parâmetros
    para o artigo.
5.  *Permissões* mostra as permissões, para cada grupo de usuários, que
    controlam o que pode ou não ser feito.

### Configurações do artigo

Além do conteúdo, um artigo possui configurações para gerenciar a
publicação, como/onde será exibido e quem poderá vê-lo quando publicado.
Em muitos casos, alguns deles serão deixados em sua configuração padrão:

<img
src="https://docs.joomla.org/images/thumb/b/bc/J4x_add_article_info_right_en.png/300px-J4x_add_article_info_right_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/b/bc/J4x_add_article_info_right_en.png 1.5x"
data-file-width="392" data-file-height="629" width="300" height="481"
alt="J4x add article info right en.png" />

1.  Selecione o **status**: Publicado, não publicado, arquivado ou
    lixeira - o padrão é *publicado*.
    1.  Selecione uma **categoria** usando o menu suspenso - este é um
        campo **necessário**. Observe que, embora necessário, se você
        não definir, o artigo ainda será salvo, mas será definido para a
        categoria, padrão do Joomla, *sem categoria*. Você pode
        adicionar uma nova categoria neste campo, digitando-a e
        **pressionando enter**.
2.  Desativa a configuração **em destaque**, exibindo ou não o artigo na
    página inicial.
3.  Selecione o nível de **acesso** para o artigo: Público, registrado,
    superusuários, etc.
4.  Selecione uma ou mais **tags** para o seu artigo. Comece a digitar
    para encontrar e selecionar tags pré-definidas ou você pode
    adicionar uma nova digitando-a e **pressionando enter**.
5.  Você pode adicionar uma **nota** que ficará visível no gerenciador
    de artigos.
6.  Você também pode adicionar uma **nota de versão** que será exibida
    no histórico de versões do artigo.

## Saving the Article

Depois de adicionar as informações e o conteúdo necessários, você pode
salvar o artigo.

Existem várias maneiras de fazer isso, dependendo do que você deseja
fazer a seguir no Joomla.

Para salvar o artigo você pode optar por *salvar*, *salvar e fechar*,
*salvar no menu* ou *salvar e novo* da seguinte forma:

<img
src="https://docs.joomla.org/images/thumb/1/1b/J4x_add_article_saving_en.png/300px-J4x_add_article_saving_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/1/1b/J4x_add_article_saving_en.png/450px-J4x_add_article_saving_en.png 1.5x, https://docs.joomla.org/images/1/1b/J4x_add_article_saving_en.png 2x"
data-file-width="500" data-file-height="234" width="300" height="140"
alt="J4x add article saving en.png" />

1.  Clique no botão **salvar** da barra de ferramentas para salvar suas
    alterações. Isso manterá o artigo aberto. É uma boa prática salvar
    regularmente seu trabalho em artigos mais longos.
2.  Clique no botão **salvar e fechar** da barra de ferramentas para
    salvar o artigo e levá-lo à lista de artigos. O botão *salvar e
    fechar* tem mais duas opções suspensas:
    1.  Clique no botão da barra de ferramentas **salvar no menu** para
        adicionar o artigo a um menu abrindo uma página **Menus: Novo
        item**.
    2.  Clique no botão **salvar e novo** da barra de ferramentas para
        salvar o artigo e abrir uma página **Artigos: Novo**. Esta opção
        economiza tempo ao adicionar vários artigos.

Uma mensagem do sistema indicará que o artigo foi salvo com sucesso.

#### Erros ao tentar salvar:

- Se você não tiver preenchido os campos obrigatórios, uma mensagem de
  erro vermelha aparecerá indicando as informações, que faltam, que você
  deve adicionar.
- Você verá uma mensagem de erro se o artigo tiver um alias que já
  exista. Você pode superar isso alterando o campo de alias.

## Dicas rápidas

- Se você não for o superusuário ou o administrador, reserve um tempo
  para entender como o site está configurado. Só porque você salvou um
  artigo não significa que ele esteja visível no site. Se as páginas de
  blog de categoria estiverem sendo usadas, atribuir a categoria correta
  exibirá o artigo. Caso contrário, um artigo precisa ser atribuído a um
  item de menu. Você pode fazer isso no artigo ou via **Menus** e depois
  **Gerenciar**.
- Tente manter os títulos dos artigos curtos e específicos.
- Embora isso possa ser feito, se houver vários usuários adicionando
  artigos ao site, evite criar novas categorias e tags nos artigos.
  Erros de ortografia e diferenças podem facilmente impedir que os
  artigos sejam exibidos onde foram planejados. A criação de categorias
  e tags em suas respectivas páginas de lista garante consistência em
  todo o site.
- Se houver necessidade, faça uso de notas de artigo. Elas podem ser
  muito úteis, especialmente quando várias pessoas adicionam artigos.
- Onde quer que você esteja no Joomla, você pode adicionar um artigo sem
  ir ao painel inicial - use o menu da barra lateral do Joomla.
