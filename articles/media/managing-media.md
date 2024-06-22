<!-- Filename: J4.x:Managing_Media / Display title: Managing Media/pt-br -->

## Introdução

No Joomla, as mídias são imagens e arquivos que aparecem como
ilustrações ou links em artigos, módulos, modelos e assim por diante.
Uma característica importante das mídias é que elas são entregues
diretamente pelo servidor web sem serem processadas pelo código do
Joomla. Isso é rápido e eficiente. Além disso, esteja ciente de que as
mídias geralmente são armazenada na pasta **imagens** do seu site
Joomla. Não confunda isso com a pasta **media**, que contém javascript e
arquivos de folha de estilo.

As mídias de imagens e arquivos é gerenciada com o componente de mídias
do Joomla. Ele permite que você organize o conteúdo das mídias em uma
árvore de pastas, carregue itens individuais, execute algumas funções
elementares de edição de imagens e coloque imagens e links diretamente
nos artigos.

## Como acessar

A partir da interface do administrador do Joomla, existem várias rotas
para abrir o componente de mídias:

- Selecione **Conteúdo **→** Mídias** no menu do administrador.
- Selecione **Painel do site **→** Mídias** no painel inicial.
- Selecione **Conteúdo do sistema de gerenciento de conteúdo
  (CMS) **→** Mídias** em uma tela de edição de artigo.

Nos dois primeiros casos, o componente de mídias aparece em uma tela de
componente normal. No último, ele aparece em uma caixa de diálogo modal.

## Captura de tela

A imagem a seguir mostra a página de mídias logo após a instalação do
Joomla, mas com a pasta cassiopeia/sampledata selecionada:

<img
src="https://docs.joomla.org/images/0/0a/J4.x-media-cassiopeia-sampledata-en.jpg"
decoding="async" data-file-width="800" data-file-height="406"
width="800" height="406"
alt="J4.x-media-cassiopeia-sampledata-en.jpg" />

## Gerenciando pastas

Os nomes das subpastas na árvore de pastas de imagens tornam-se parte do
url da imagem, por isso é importante para fins de vinculação e
otimização de mecanismos de pesquisa que os nomes estejam em
conformidade com uma convenção:

- todas as letras minúsculas
- sem espaços ou pontuação
- se necessário, use um sinal de menos para criar palavras legíveis por
  humanos, por exemplo árvores-decíduas em vez de árvores_decíduas.

Antes de criar muito conteúdo para o seu site, pode valer a pena pensar
em como você pode categorizar seu conteúdo e talvez criar uma árvore de
pastas de imagens semelhante à sua árvore de categorias. Caso contrário,
você pode acabar com um número muito grande de imagens e arquivos na
raiz da sua árvore de imagens e isso se tornará difícil de gerenciar. Se
você decidir mover as imagens para uma estrutura melhor posteriormente,
terá que encontrar os links para essas imagens em seus artigos e
alterá-los. Isso pode ser uma tarefa demorada e assustadora!

### Navegação de pastas

Use a árvore de pastas na coluna **local** para selecionar uma pasta. No
caso ilustrado acima, a pasta cassiopeia foi selecionada primeiro. Isso
revelou a pasta sampledata que foi então selecionada para mostrar seu
conteúdo.

A localização atual também é indicada nas trilhas acima das imagens.
Nesse caso **images **→** cassiopeia **→** sampledata**.

Se você selecionar uma pasta diferente, a pasta anterior no mesmo nível
será fechada.

### Criando uma pasta

- Selecione a pasta pai na qual a nova pasta deve ser criada.
- Selecione o botão **criar nova pasta**.
- Na janela pop-up *criar nova pasta*, digite um nome para a pasta no
  campo **nome da pasta**.
- Clique no botão **criar**.
- A nova pasta aparecerá na pasta pai selecionada junto com uma mensagem
  verde de sucesso do sistema.

### Excluindo uma pasta

***Aviso: excluir uma pasta também excluirá todo o conteúdo da pasta!***

- Selecione o pai da pasta a ser excluída usando a árvore de diretórios
  mostrada em **local**. Isso mostrará todas as pastas e arquivos no
  pai.
- Mova o cursor sobre a pasta a ser excluída na área de mídias. Ele
  ficará cinza e um botão branco aparecerá próximo ao canto superior
  esquerdo.
- Selecione o botão branco. Uma marca verde aparecerá para indicar que
  está selecionado.
- Selecione o botão **excluir** na barra de ferramentas.
- Na caixa de diálogo pop-up para **confirmar exclusão** selecione o
  botão **excluir**. A pasta será excluída junto com todos os seus
  arquivos, subpastas e seus arquivos.

A pasta selecionada para exclusão é ilustrada abaixo:

<img
src="https://docs.joomla.org/images/4/40/J4.x-media-delete-folder-en.jpg"
decoding="async" data-file-width="800" data-file-height="201"
width="800" height="201" alt="J4.x-media-delete-folder-en.jpg" />

## Barra de ferramentas da área de mídias

Esta é a barra acima da lista de imagens, arquivos e pastas que possui
botões para diversas tarefas.

### Caixa de seleção

Uma caixa de seleção que permite selecionar todos os itens da pasta
exibida na área de mídias. Você pode querer usá-lo para excluir todos os
itens atuais sem excluir a pasta.

### Trilhas

Use os nomes das pastas acima da área de mídias para retroceder na
hierarquia de pastas.

Clique duas vezes no nome de uma pasta na área de mídias para abrir essa
pasta.

### Pesquisa

Se você tiver uma longa lista de imagens e arquivos, poderá pesquisar
itens que contenham qualquer grupo de caracteres. A pesquisa é
progressiva: à medida que você adiciona caracteres ao termo de pesquisa,
a lista é reduzida apenas àquelas que contêm essa sequência de
caracteres.

### Ampliar

Use os botões de ampliação para ampliar ou reduzir o tamanho da
miniatura. Dependendo do tamanho da tela, você poderá ver 2, 4, 6 ou 8
imagens em miniatura lado a lado.

### Exibições de lista ou miniatura

Na visualização de miniaturas, selecione o símbolo de lista para
alternar para a visualização de lista. Na exibição de lista, selecione o
símbolo de miniatura para alternar para a exibição de miniatura. Na
visualização de lista você verá informações sobre tamanho e dimensões da
imagem, entre outros dados.

### Informações

Selecione o ícone de informações para abrir um painel lateral mostrando
informações sobre o que estiver selecionado.

## Outras informações

Nesta série de tutoriais:

-  Gerenciando
  mídias
-  Mídia: Carregar, excluir,
  renomear
-  Mídia: corte, redimensionamento, rotação de
  imagens
-  Mídia:
  opções
- \[\[S:MyLanguage/J4.x:Media:\_Uploading_SVG_files\|

\]\]
