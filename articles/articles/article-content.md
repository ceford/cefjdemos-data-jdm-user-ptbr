<!-- Filename: J4.x:Adding_a_New_Article / Display title: Artigo: Editar - Conteúdo -->

## Introdução

*Adicionar um Artigo* foi abordado em um artigo de *Introdução*. Este é o primeiro de uma série de artigos que fornece mais detalhes sobre o formulário *Artigo: Editar*. Ele abrange a aba *Conteúdo* e alguns aspectos do editor TinyMCE, o editor padrão fornecido com o Joomla.

A captura de tela a seguir mostra o formulário de edição com um artigo que já foi salvo.

![O formulário de edição de conteúdo](../../../en/images/articles/articles-edit-content.png)

## Entrada de Dados

O formulário de edição do artigo possui painéis com abas. Um novo artigo tem a aba **Conteúdo** selecionada por padrão. Caso contrário, a última aba aberta é selecionada.

### O campo Título

O campo **Título** é *Obrigatório* e é usado sempre que o título do artigo é exibido. Este é o único campo que deve conter algum texto para poder salvar um formulário de edição.

Os títulos devem ser curtos, mas descritivos do conteúdo do artigo, pois aparecem em listas e itens de menu onde o espaço é limitado.

Os títulos não precisam ser exclusivos, embora seja melhor que sejam. Por exemplo, se você selecionar *Salvar como Cópia* na lista suspensa *Salvar e Fechar*, o processo de salvamento irá salvar o artigo atual e gerar um novo com um número adicionado ao Título e Apelido. Você pode remover o número do Título, mas não do Apelido, e *Salvar* a cópia. Isso gera dois artigos com o mesmo título exibido.

### O campo Apelido

O campo *Apelido* geralmente é deixado em branco. Quando o artigo é salvo, o Apelido é gerado a partir do título ao convertê-lo totalmente para minúsculas e substituir caracteres não alfanuméricos por hifens.

Se você alterar o título do artigo, poderá deletar o Apelido e um novo será gerado. Se o Apelido foi usado para se referir ao artigo em links internos e externos, isso irá quebrar os links. Portanto, é melhor não alterar o Apelido de um artigo antigo.

### A Aba de Conteúdo - Texto do Artigo

A captura de tela acima mostra o texto do artigo em um editor WYSIWYG que se parece com um processador de texto. No entanto, você deve estar ciente de que o texto do artigo é armazenado como HTML e o campo de entrada de dados é realmente uma área de texto contendo esse HTML. Você pode vê-lo por si mesmo selecionando o botão *Alternar Editor* abaixo da área de edição. O Editor é, na verdade, uma aplicação JavaScript que exibe novamente o HTML para torná-lo fácil de ler e manipular.

#### Tags e Atributos HTML Não Permitidos

Tanto o Joomla quanto o editor TinyMCE têm configurações que não permitem certas tags e atributos HTML. Por exemplo, a lista padrão proibida do Joomla inclui *iframe*, portanto, se você tentar incluir essa tag em um artigo, ela será removida silenciosamente ao salvar. Filtros de texto são configurados em *Configuração Global*. O plugin TinyMCE possui uma opção para *Usar Filtro de Texto Joomla*. Se configurado para *Desligado*, ele lista *script,applet,iframe* como *Elementos Proibidos*.

#### Barras de Ferramentas do Editor

Acima da área de texto estão as linhas de Barras de Ferramentas. Duas são exibidas por padrão. As outras podem ser alternadas selecionando o símbolo de reticências (...) no final da segunda Barra de Ferramentas. As Barras de Ferramentas podem ser configuradas para mostrar diferentes barras e conteúdos de barra para diferentes grupos de usuários.

Existem muitas ferramentas para descrever cada uma aqui. Isso criaria um "palheiro" para você procurar uma "agulha". Apenas explore!

No entanto, existem alguns recursos que merecem explicação extra.

#### Conteúdo do CMS

Este botão revela uma lista suspensa que permite a inclusão de itens em um artigo obtidos de outro lugar no CMS.

- **Artigo** Este link revela uma lista pop-up de artigos. Selecione um artigo para incluir um link para esse artigo no artigo atual.
- **Contato** Inclua um link para um Contato no artigo atual.
- **Campo** Inclua um campo no artigo. Ele é exibido como `{field 1}`.
- **Mídia** Inclua uma imagem ou arquivo de um componente de Mídia pop-up.
- **Menu** Inclua um link para um item de Menu em uma lista pop-up de Menu.
- **Quebra de Página** Há um prompt para um *Título da Página* e um *Apelido do Índice*. Esse recurso é usado para dividir documentos longos em várias páginas.
- **Leia Mais** Um separador *Leia Mais...* é inserido na posição do cursor. Escolha uma divisão entre parágrafos antes da seleção.

#### Links Externos

O item **Inserir** na primeira Barra de Ferramentas tem opções para inserir um *Link...*, *Imagem...* ou *Mídia...*. Esses são para itens externos, então esteja preparado com o URL do item a ser usado.

### A Aba de Conteúdo - Configurações

A aba **Conteúdo** é ocupada majoritariamente pelo editor TinyMCE.

Ao lado do conteúdo, há campos para gerenciar a publicação, como e onde o artigo será exibido e quem pode vê-lo quando publicado. Na maioria dos casos, essas configurações podem ser deixadas nos valores padrão.

1.  **Status** *Publicado*, *Não Publicado*, *Arquivado* ou *Lixeira* - o padrão é *Publicado*.
2.  **Categoria** Este é um campo *Obrigatório*, mas será padrão para *Sem Categoria*. Você pode selecionar uma categoria da lista ou digitar alguns caracteres de um nome de categoria para encurtar a lista de categorias para escolher.
3.  **Em Destaque** Alternar entre *Não* e *Sim* para exibir o artigo na página inicial se esta usar um layout de *Artigos em Destaque*.
4.  **Acesso** O nível de acesso pode ser alterado para restringir o artigo a Grupos de Usuários atribuídos a níveis de *Acesso* específicos: *Público*, *Convidado*, *Registrado*, *Especial* ou *Super Usuários*.
5.  **Tags** Comece a digitar para encontrar e selecionar tags predefinidas ou você pode adicionar uma nova digitando e **pressionando enter**.
6.  **Nota** Qualquer comentário sobre este artigo que será visível sob o Título na página da lista de Artigos.
7.  **Nota de Versão** Adicione comentários para indicar o que mudou nesta versão. Isso é exibido na caixa de diálogo modal *Versões* e o campo retorna ao vazio após salvar.

### Outras Abas

**Você pode não ver todas as abas a seguir** pois um Administrador do Site pode ocultar algumas para ajudar a manter a consistência do layout do artigo em todo o site. Você também pode ver abas adicionais para *Campos Personalizados*, se tiverem sido configuradas.

1.  **Imagens e Links** permite que você configure uma imagem de introdução e destacada e/ou links para aparecer em posições predefinidas. Isso pode ser usado se seu artigo será exibido dentro de um blog de categoria.
2.  **Opções** permite que você especifique o layout do artigo e informações associadas como título, categoria, tags, detalhes de publicação, etc. Isso é normalmente definido globalmente, mas pode ser específico ao artigo através dessas opções.
3.  **Esquema** é um método para adicionar metadados a um artigo. É usado por robôs, mas não visto por humanos.
3.  **Publicação** permite que você configure datas e horários de publicação para agendar a publicação de um artigo. Por padrão, quando um artigo é salvo, ele será publicado imediatamente. Você também pode configurar os Metadados do artigo.
4.  **Configurar Tela de Edição** permite que você mostre ou oculte parâmetros para o artigo.
5.  **Permissões** mostra as permissões para cada grupo de usuários que controlam o que pode ou não ser feito.

Existem artigos separados sobre cada uma dessas abas.

## Salvando o Artigo

Depois de adicionar as informações e o conteúdo necessários, você pode salvar o artigo. Existem várias maneiras de fazer isso, dependendo do que você deseja fazer a seguir no Joomla.

Para salvar o artigo, você pode escolher entre *Salvar* ou *Salvar & Fechar*. Este último possui opções no menu suspenso de *Salvar & Novo*, *Salvar no Menu* e *Salvar como Cópia*.

- **Salvar** Salva o artigo e o mantém aberto para mais edições. 
  É uma boa prática salvar seu trabalho regularmente em artigos mais longos.
- **Salvar & Fechar** Salva o artigo e vai para a lista de Artigos. O botão Salvar & Fechar tem mais opções no menu suspenso:
    - **Salvar & Novo** Salva o artigo e, em seguida, abre uma página **Artigos: Novo**. 
      Esta opção economiza tempo ao adicionar múltiplos artigos.
    - **Salvar no Menu** Salva o artigo e abre uma página **Menus: Novo Item**.
    - **Salvar como Cópia** Salva o artigo, em seguida, abre uma página **Artigos: Editar** com um número entre parênteses acrescentado ao título e o mesmo número seguido de um hífen, -2 por exemplo, no campo de alias. Você pode alterar o título e alterar ou excluir o alias do novo artigo que já foi criado.

Uma mensagem do sistema indicará que o artigo foi salvo com sucesso.

### Erros ao tentar salvar:

- Se você não completou os campos obrigatórios, uma mensagem de erro em vermelho aparecerá indicando a informação que está faltando e que você deve adicionar.
- Você verá uma mensagem de erro se o artigo tiver um alias que já existe. Você pode resolver isso alterando o campo de alias.

## Dicas

- Se você não é o Super Usuário ou Administrador, reserve um tempo para
  entender como o site está configurado. Só porque você salvou um
  artigo não significa que ele está visível no site. Se estiverem sendo
  usadas páginas de Blog de Categoria, atribuir a categoria correta exibirá 
  o artigo. Caso contrário, um artigo precisa ser atribuído a um item de menu. 
  Você pode fazer isso no próprio artigo ou via o menu **Menus** do Administrador.
- Tente manter os títulos dos artigos curtos e específicos.
- Embora seja possível, se houver vários usuários adicionando artigos ao
  site, evite criar novas categorias e tags nos artigos.
  Erros de ortografia e diferenças podem facilmente impedir que os artigos sejam 
  exibidos no local correto. Criar categorias e tags na respectiva página da lista 
  garante consistência em todo o site.
- Se necessário, utilize notas de artigo. Elas podem ser muito
  úteis, especialmente quando várias pessoas adicionam artigos.
- Onde quer que esteja no Joomla, você pode adicionar um artigo sem ir até o
  Painel de Controle - use o Menu do Administrador do Joomla.

