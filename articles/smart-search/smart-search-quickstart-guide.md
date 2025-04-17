<!-- Filename: Smart_Search_quickstart_guide / Display title: Guia de Início Rápido da Busca Inteligente  -->

## Contexto

A busca tem sido um recurso do Joomla! desde seus primeiros dias. Ela permitia
aos usuários buscar palavras ou frases no banco de dados e retornar resultados
na ordem em que eram encontrados. Esse tipo de busca foi removido e substituído pela Busca Inteligente, que pré-indexa palavras significativas e usa algoritmos de pontuação e filtragem para ajudar a retornar os melhores resultados. A Busca Inteligente está habilitada por padrão no Joomla 4 e 5.

### Fique atento

Se você tiver itens de conteúdo que não estão disponíveis para visualização pública, o recurso de autocompletar ainda mostrará os termos contidos nesses itens de conteúdo. Os próprios itens de conteúdo não podem ser visualizados e não serão listados nos resultados de busca, mas se revelar a presença de uma palavra ou frase em um item de conteúdo restrito for uma preocupação, você deve desabilitar o autocompletar. Para desabilitar o autocompletar, use o seguinte procedimento:

1.  Faça login no Administrador.
2.  Selecione **Componentes → Busca Inteligente**.
3.  Selecione o botão **Opções** na barra de ferramentas.
4.  Altere *Sugestões de Busca* de **Mostrar** para **Ocultar**.
5.  Selecione **Salvar & Fechar**.

## Preparando plugins de Busca Inteligente

Para que o conteúdo seja exibido nos resultados de busca, ele deve primeiro ser indexado por um dos plugins de Busca Inteligente. Antes de iniciar o indexador, é recomendável que você revise os plugins disponíveis e desabilite aqueles que não serão necessários para o seu site. Para revisar os plugins de Busca Inteligente disponíveis, siga o procedimento abaixo:

1. Faça login no Administrador.
2. Selecione **Plugins** no *Painel Inicial*.
3. Filtre os plugins usando o item **finder** da lista **- Selecionar Tipo -**.
4. Revise a lista de plugins e desabilite aqueles que não serão necessários para o seu site selecionando o ícone de tique verde na coluna de Status do plugin. Isso deve mudar para um símbolo de cruz/círculo cinza para indicar que o plugin está desabilitado.

## Executando o Indexador

Após revisar os plug-ins de busca, é hora de iniciar o indexador de pesquisa inteligente. Isso irá escanear o conteúdo do seu site e construir um índice que permitirá uma busca rápida e inteligente pelos visitantes do seu site. Existem duas maneiras de executar o indexador:

* Pelo menu **Administrador / Pesquisa Inteligente / Índice**. Isto é adequado para sites menores.
* Pela Linha de Comando. Isto é adequado para sites maiores e não deve resultar em falhas por tempo de execução. No entanto, sites muito grandes podem realmente precisar de um serviço de busca externo.

### Indexação pela interface do Administrador

1. Faça login no Administrador.
2. Selecione os itens de menu **Componentes → Pesquisa Inteligente → Índice**.
3. Selecione o botão **Índice** na barra de ferramentas para iniciar o indexador. Isto fará com que uma janela modal seja carregada com algumas informações de status do indexador e uma barra de progresso.

Dependendo do tamanho do seu site, a indexação pode levar de alguns minutos a algumas horas para ser concluída. O indexador usa requisições AJAX para completar o processo geral em pequenas partes para evitar problemas de timeout e memória. A indexação é concluída quando a barra de progresso desaparece e a janela modal se fecha.

### Indexação pela CLI

1. Abra uma janela de terminal.
2. Navegue até a pasta cli na raiz do seu site.
3. Use o seguinte comando:<br>
   php joomla.php finder:index
4. Quando o indexador tiver terminado, vá para a página de Conteúdo Indexado do Administrador da Pesquisa Inteligente.

## Conteúdo Indexado

A página de Conteúdo Indexado lista todo o conteúdo indexado. Se você preferir que itens específicos não sejam exibidos nos resultados de busca, pode despublicá-los do banco de dados do Smart Search selecionando a caixa de seleção ao lado do título do item e, em seguida, pressionando o botão Despublicar.

**NOTA IMPORTANTE**: Se o seu site tiver uma grande quantidade de conteúdo, ou itens de conteúdo particularmente grandes, ou tiver espaço em disco restrito, você deve ler sobre [Pesquisa Inteligente em sites grandes](jdocmanual?article=user/smart-search/smart-search-on-large-sites).

## Expondo a Busca Inteligente aos Usuários do Site

Agora que o índice de Busca Inteligente está preparado e pronto, você precisa expor a Busca Inteligente aos usuários do seu site. A Busca Inteligente oferece duas maneiras de fazer isso:

### A Interface do Módulo

A Busca Inteligente inclui um módulo que pode ser ativado para exibir um formulário de busca simples em qualquer página, praticamente em qualquer posição. Para habilitar o módulo de Busca Inteligente use o seguinte procedimento:

1. Faça login no Administrador.
2. Selecione o item de menu Extensões → Gerenciador de Módulos.
3. Clique no botão Novo na barra de ferramentas do Gerenciador de Módulos.
4. Selecione "Módulo de Busca Inteligente" na lista de tipos de módulo exibidos.
5. Configure o módulo, pelo menos, inserindo um título, selecionando a posição do módulo e ajustando as páginas em que ele será exibido, se desejado. Opções adicionais de configuração do módulo são descritas na tela de ajuda do módulo de Busca Inteligente.
6. Selecione o botão Salvar na barra de ferramentas para publicar o módulo.

### A Interface do Item de Menu

A Busca Inteligente também pode ser vinculada por meio de um item de menu do Joomla para que os usuários possam navegar diretamente para o formulário de busca principal. Para criar um link de item de menu para a Busca Inteligente, use o seguinte procedimento:

1. Faça login no Administrador.
2. Selecione o item de menu Extensões → Gerenciador de Módulos.
3. Pressione o botão Novo na barra de ferramentas do Gerenciador de Menus.
4. Clique no botão Selecionar ao lado do campo Tipo de Item de Menu.
5. Selecione "Busca" embaixo da entrada "Busca Inteligente" na lista de tipos de item de menu exibidos.
6. Configure o item de menu, pelo menos, inserindo um Título para o Menu e ajustando o item pai, se desejado.
7. Selecione o botão Salvar na barra de ferramentas para publicar o item de menu.

## Testando, Testando, Testando

Para testar a Pesquisa Inteligente, navegue até um dos itens do menu que você criou e insira uma consulta no formulário de pesquisa ou insira uma consulta em uma das instâncias do módulo de Pesquisa Inteligente. Você deve ser direcionado a uma lista de resultados de pesquisa, se algum for encontrado para a palavra ou frase que você inseriu. Se nenhum resultado for encontrado, uma mensagem será exibida indicando que nenhum resultado pôde ser encontrado. Se nenhum resultado for encontrado e o sistema tiver uma sugestão de pesquisa com base no seu termo, a frase de pesquisa sugerida será exibida acima da mensagem indicando que nenhum resultado pôde ser encontrado.

*Traduzido por openai.com*

