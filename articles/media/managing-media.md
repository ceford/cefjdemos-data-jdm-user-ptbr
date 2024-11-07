<!-- Filename: J4.x:Managing_Media / Display title: Gerenciando Mídia -->

## Introdução

No Joomla, mídias são imagens e arquivos que aparecem como ilustrações ou links em artigos, módulos, templates e assim por diante. Uma característica importante das mídias é que elas são entregues diretamente pelo servidor web sem serem processadas pelo código do Joomla. Isso é rápido e eficiente. Além disso, esteja ciente de que as mídias geralmente são armazenadas na pasta **images** do seu site Joomla. Não confunda isso com a pasta **media**, que contém arquivos javascript e de folha de estilo.

As mídias de imagem e arquivo são gerenciadas com o componente Mídia do Joomla. Ele permite que você organize o conteúdo de mídia em uma árvore de pastas, faça upload de itens individuais, execute algumas funções elementares de edição de imagem e insira imagens e links diretamente em artigos.

## Como Acessar

A partir da interface do Administrador do Joomla, há várias maneiras de abrir o componente de Mídia:

- Selecione **Conteúdo → Mídia** no menu do Administrador.
- Selecione **Painel do Site → Mídia** no Painel Inicial.
- Selecione **Conteúdo CMS → Mídia** na tela de edição de um artigo.

Nos dois primeiros casos, o componente de Mídia aparece em uma tela normal de componente. No último, ele aparece em uma caixa de diálogo modal.

## Captura de Tela

A imagem a seguir mostra a página de Mídia logo após a instalação do Joomla, mas com a pasta cassiopeia/sampledata selecionada. Uma pasta *files* foi adicionada para armazenar arquivos que não são imagens, e uma pasta extra chamada *garbage* foi adicionada para ilustrar a exclusão de pastas:

![Página de Mídia mostrando dados de exemplo cassiopeia](../../../en/images/media/media-sample-data-cassiopeia.png)

## Gerenciando Pastas

Os nomes das subpastas na árvore de pastas de suas imagens tornam-se parte da URL da imagem. Por isso, é importante para fins de linkagem e otimização para motores de busca que os nomes sigam uma convenção:

- todas em letras minúsculas
- sem espaços ou pontuação
- se necessário, use um hífen para criar palavras legíveis, por exemplo, arvores-de-folhas-caducas em vez de arvores_de_folhas_caducas.

Antes de criar muito conteúdo para o seu site, pode ser benéfico pensar com antecedência sobre como categorizar seu conteúdo e, talvez, criar uma árvore de pastas de imagens semelhante à sua árvore de categorias. Caso contrário, você pode acabar com um número muito grande de imagens e arquivos na raiz da sua árvore de imagens, o que será difícil de gerenciar. Se você decidir mover as imagens para uma estrutura melhor mais tarde, terá que encontrar os links para essas imagens em seus artigos e alterá-los. Isso pode ser uma tarefa demorada e assustadora!

### Navegação de Pasta

Use a árvore de pastas na coluna **Local** para selecionar uma pasta. No caso ilustrado acima, a pasta cassiopeia foi selecionada primeiro. Isso revelou a pasta *sampledata*, que foi então selecionada para mostrar seu conteúdo.

A localização atual também é indicada no breadcrumb acima das imagens. Neste caso **imagens → cassiopeia → sampledata**.

Se você selecionar uma pasta diferente, a pasta anterior no mesmo nível será fechada.

### Criando uma pasta

- Selecione a pasta pai em que a nova pasta deve ser criada.
- Selecione o botão **Criar Nova Pasta**.
- Na janela pop-up *Criar Nova Pasta*, insira um nome para a pasta no campo **Nome da Pasta**.
- Clique no botão **Criar**.
- A nova pasta aparecerá na pasta pai selecionada junto com uma mensagem de sistema verde de Sucesso.

### Excluindo uma pasta

**Aviso: excluir uma pasta também excluirá todo o conteúdo da pasta!**

- Selecione os pais da pasta a ser excluída usando a árvore de diretórios exibida em **Local**. Isso mostrará todas as pastas e arquivos no pai.
- Mova o cursor sobre a pasta a ser excluída na área de mídia. Ela ficará cinza e um botão aparecerá perto do canto superior esquerdo.
- Selecione o botão. Uma marca de seleção aparecerá para indicar que está selecionada.
- Selecione o botão **Excluir** da Barra de Ferramentas.
- Na caixa de diálogo **Confirmar Exclusão**, selecione o botão **Excluir**. A pasta será excluída junto com todos seus arquivos, subpastas e seus arquivos.

A pasta selecionada para exclusão é ilustrada abaixo:

![Página de mídia mostrando pasta de lixo](../../../en/images/media/media-sample-data-garbage-select.png)

## Barra de Ferramentas da Área de Mídia

Esta é a barra acima da lista de imagens, arquivos e pastas que possui botões para uma variedade de tarefas.

### Caixa de Seleção

Uma caixa de seleção que permite selecionar todos os itens na pasta exibida na área de mídia. Você pode usá-la para excluir todos os itens atuais sem excluir a pasta.

### Navegação por Caminho (Breadcrumbs)

Use os nomes das pastas acima da área de mídia para voltar na hierarquia de pastas.

Clique duas vezes no nome de uma pasta na área de mídia para abrir essa pasta.

### Pesquisa

Se você tem uma longa lista de imagens e arquivos, pode pesquisar por itens que contenham qualquer grupo de caracteres. A pesquisa é progressiva: à medida que você adiciona caracteres ao termo de pesquisa, a lista é reduzida apenas àqueles que contêm essa sequência de caracteres.

### Ampliar

Use os botões de ampliação para aumentar ou reduzir o tamanho das miniaturas. Dependendo do tamanho da sua tela, você pode ver 2, 4, 6 ou 8 imagens em miniatura lado a lado.

### Visualizações em Lista ou Miniatura

Na visualização em miniatura, selecione o símbolo de lista para alternar para a visualização em lista. Na visualização em lista, selecione o símbolo de miniatura para alternar para a visualização em miniatura. Na visualização em lista, você verá informações sobre o tamanho e dimensões da imagem, entre outros dados.

### Ícone de Informação

Selecione o ícone de Informação para abrir um painel lateral mostrando informações sobre o que quer que esteja selecionado.

*Traduzido por openai.com*

