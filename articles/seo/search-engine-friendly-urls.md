<!-- Filename: Search_Engine_Friendly_URLs / Display title: Localizadores uniformes de recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs) -->

**Amigável para os mecanismos de pesquisas (SEF)**, **legível por
humanos** ou
<a href="https://en.wikipedia.org/wiki/pt:Slug_(programa%C3%A7%C3%A3o)"
class="extiw" title="wikipedia:pt:Slug (programação)">localizadores
uniformes de recursos (URLs) limpos</a> são localizadores uniformes de
recursos (URLs) que fazem sentido tanto para humanos quanto para
mecanismos de pesquisa porque explicam o caminho para a página
específica para a qual apontam. Desde a versão 1.5, Joomla! é capaz de
criar e analisar localizadores uniformes de recursos (URLs) em qualquer
formato, incluindo localizadores uniformes de recursos (URLs) amigáveis
para mecanismos de pesquisas (SEFs). Isso não depende da reescrita de
localizadores uniformes de recursos (URLs) executada pelo servidor web,
então funciona mesmo que o Joomla! seja executado um servidor diferente
do Apache com o módulo mod_rewrite. Os localizadores uniformes de
recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs) seguem um
certo padrão fixo, mas o usuário pode definir um  texto descritivo curto
(alias) para cada
segmento dos localizadores uniformes de recursos (URLs).

Internamente, a parte local de um localizador uniforme de recursos (URL)
amigável para mecanismos de pesquisas (SEF) (a parte após o nome do
domínio) é chamada de **rota**. A criação e processamento dos
localizadores uniformes de recursos (URLs) amigáveis para mecanismos de
pesquisas (SEFs) é, portanto, chamado de **roteamento**, e o código
relevante é chamado de **roteador**.

Um bom exemplo de roteamento é o localizador uniforme de recursos (URL)
para o artigo "Bem-vindo ao Joomla!" nos dados de amostras.

- Sem os localizadores uniformes de recursos (URLs) amigáveis para
  mecanismos de pesquisas (SEFs) ativados, o localizador uniforme de
  recursos (URL) é
  `http://www.example.com/index.php?option=com_content&view=article&id=1:welcome-to-joomla&catid=1:latest-news&Itemid=50`
- Com os localizadores uniformes de recursos (URLs) amigáveis para
  mecanismos de pesquisas (SEFs) ativados e o mod_rewrite desativado, é
  `http://www.example.com/index.php/the-­news/1-­latest­-news/1­-welcome­-to­-joomla`
- Com os localizadores uniformes de recursos (URLs) amigáveis para
  mecanismos de pesquisas (SEFs) e o mod_rewrite, ambos ativados, é
  `http://www.example.com/the-­news/1­-latest-­news/1-­welcome-­to­-joomla`

Os localizadores uniformes de recursos (URLs) amigáveis para mecanismos
de pesquisas (SEFs) localizadores uniformes de recursos (URLs) amigáveis
para mecanismos de pesquisas (SEFs) podem ser ativados ativando a opção
**localizadores uniformes de recursos (URLs) amigáveis para mecanismos
de pesquisas (SEFs)** nas *configuração globais*. Esta opção está
ativada por padrão desde o Joomla! 1.6. Consulte [Ativando localizadores
uniformes de recursos (URLs) amigáveis para mecanismos de pesquisas
(SEFs)](https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs/pt-br "Enabling Search Engine Friendly (SEF) URLs/pt-br")
para obter mais informações.

## Perguntas frequentes

### O que significam os números nos localizadores uniformes de recursos (URLs)

Ao comparar os localizadores uniformes de recursos (URLs) antigo e novo,
podemos ver números no localizador uniforme de recursos (URL) antigo,

    http://www.example.com/index.php?option=com_content&view=article&id=1:welcome-to-joomla&catid=1:latest-news&Itemid=50

mas também no novo localizador uniforme de recurso (URL):

    http://www.example.com/the-­news/1­-latest-­news/1-­welcome-­to­-joomla

Esses números são os parâmetros necessários para o Joomla! obter o
localizador uniforme de recurso (URL) interno e mostrar a página que
você deseja ver. (Neste caso, o primeiro numeral é o ID da categoria e o
segundo numeral é o ID do artigo.)

### Não há mais `index.php` no localizadores uniformes de recursos (URLs). Posso excluir o arquivo agora?

Não! Os localizadores uniformes de recursos (URLs) não contêm mais o
`index.php` pois, internamente, o mod_rewrite só redireciona você para o
caminho original sem mostrá-lo.

### O que é o valor alias? E como ele é criado?

O alias é listado abaixo do campo "título" em artigos, categorias,
seções e itens de menu. O Joomla! pode criar automaticamente o alias
para você. Um alias automático começa com o título. Todas as letras
maiúsculas são alteradas para minúsculas. Espaços e caracteres especiais
que não são permitidos em localizadores uniformes de recursos (URLs),
são alterados para traços.

### Quero especificar meu próprio valor para alias.

Se você não quiser o alias fornecido pelo Joomla!, você pode inserir um
valor de sua escolha nesse campo. Muitos acreditam que usar boas
palavras-chave em seus localizadores uniformes de recursos (URLs) ajuda
na otimização dos mecanismos de pesquisas. Você pode fazer isso
incluindo essas palavras-chave em seu título e permitindo que o Joomla!
crie o alias ou criando você mesmo o alias.

### Como o alias é usado em localizadores uniformes de recursos (URLs)?

Para itens de menus, o Joomla! usa os aliases como os slugs dos
localizadores uniformes de recursos (URLs). Suponha que você use as duas
primeiras opções dos localizadores uniformes de recursos (URLs)
amigáveis para mecanismos de pesquisas (SEFs) e crie um item de menu
chamado "produtos". Seu localizador uniforme de recursos (URL) seria
example.com/produtos.

O Joomla! também usa os valores de chaves primárias de dados nos
localizadores uniformes de recursos (URLs) para ajudar o roteador a
navegar para a página correta. Continuando com o exemplo anterior, se o
item de menu de seus produtos fosse para um blog de artigos/categorias,
o link para o título do artigo e/ou o link leia mais teria três partes:

- O localizador uniforme de recursos (URL) do item de menu -
  example.com/produtos;
- Além disso, a chave primária para a categoria e o alias da categoria -
  32-fruta;
- Além disso, a chave primária para o artigo e o alias do artigo -
  1-laranja;


O localizador uniforme de recursos (URL) completo é:
`http://example.com/produtos/32-fruta/1-laranja`

### Como posso me livrar dos números nos localizadores uniformes de recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs)?

Os números nos localizadores uniformes de recursos (URLs) amigáveis para
mecanismos de pesquisas (SEFs) são necessários para o roteador do
Joomla! saber como direcionar o tráfego do site. Uma vez que a lógica do
roteador se estabilize, plug-ins de sistema de terceiros simples podem
ser desenvolvidos para aumentar os recursos do roteador, permitindo mais
opções. Nesse momento, os números provavelmente serão removidos dos
localizadores uniformes de recursos (URLs).

## Formatos de rota e o mecanismo de roteamento

*Esta seção descreve o mecanismo de roteamento principal (incorporado)
do Joomla!. As extensões de roteamento podem alterar a maneira como as
rotas são criadas em seu sistema.*

### Formatos de rota

Para descrever o mecanismo de roteamento do Joomla! com mais detalhes,
primeiro precisamos definir o que chamamos de **rota**. Suponha que o
Joomla! tenha sido instalado em `http://example.com/sites/primeiro/`. O
caminho de instalação é geralmente chamado de **localizador uniforme de
recursos (URL) base**. Um possível exemplo de localizador uniforme de
recursos (URL) é
`http://example.com/sites/primeiro/produtos/32-fruta/1-laranja`. A
primeira parte deste localizador uniforme de recursos (URL) é o
localizador uniforme de recursos (URL) base mencionado acima e nem o
Joomla! nem qualquer roteador componente pode criar localizadores
uniformes de recursos (URLs) com uma primeira parte diferente. A segunda
parte, `produtos/32-fruta/1-laranja`, é uma **rota**, composta por três
**segmentos**.

O primeiro segmento de uma rota é, para localizadores uniformes de
recursos (URLs) regulares, o alias de um item de menu. Diz-se que os
localizadores uniformes de recursos (URLs) amigáveis para mecanismos de
pesquisas (SEFs) são **roteados através** desse item de menu. Os demais
segmentos são determinados inteiramente pelo roteador do componente que
fornece o tipo do item de menu. O tipo de item de menu *Categoria -
Blog*, por exemplo, é fornecido pelo componente de
conteúdo e,
portanto, o roteador desse componente é responsável por construir e
analisar os segmentos restantes.

Também é possível (para extensões) solicitar ao sistema que crie uma
rota sem fornecer um item de menu para percorrer. Nesse caso, o sistema
geralmente decidirá criar uma rota especial que tenha a palavra
`component` como primeiro segmento. Essas rotas são criadas usando um
formato fixo: o nome do componente (sem o `com_` inicial) é selecionado
como o segundo segmento e quaisquer parâmetros como os outros segmentos.

### Limitações

É importante notar que a criação de um item de menu é a "única" maneira
para um usuário do Joomla! definir uma rota que leva a um componente
específico. É, no entanto, possível criar uma rota sem apresentá-la no
site (em um menu). Um método frequentemente aplicado é criar um item de
menu em um menu que não é exibido em nenhum lugar. Esse menu geralmente
é chamado de <a
href="https://docs.joomla.org/index.php?title=Menu/pt-br&amp;action=edit&amp;redlink=1"
class="new" title="Menu/pt-br (page does not exist)">menu oculto</a>.

O parágrafo anterior implica que não é possível tornar um componente
responsável pelo manuseio de todas as rotas. Por exemplo, não é possível
especificar que o localizador uniforme de recursos (URL)
`http://example.com/o_alias` deva exibir o item "conteúdo" com o alias
`o_alias`, onde `o_alias` pode ser qualquer palavra. Se isso precisar
ser feito para um pequeno número de artigos, os itens de menu podem ser
criados manualmente para eles. Caso contrário, uma extensão de
roteamento é necessária.

Esse mecanismo de roteamento, portanto, não é tão flexível quanto os
usuários às vezes exigem. Por outro lado, tem uma grande vantagem: reduz
a chance de rotas ambíguas (rotas que podem levar a duas páginas
diferentes). Como o primeiro segmento de uma rota é sempre um alias de
item de menu, o sistema sabe imediatamente qual roteador de componente
deve ser usado para analisá-lo.

## Detalhes de implementação

### Manipulando rotas

*Esta seção descreve a implementação de roteamento. Se você for um
desenvolvedor de componentes, consulte <a
href="https://docs.joomla.org/index.php?title=Supporting_SEF_URLs_in_your_component/pt-br&amp;action=edit&amp;redlink=1"
class="new"
title="Supporting SEF URLs in your component/pt-br (page does not exist)">Suportando
localizadores uniformes de recursos (URLs) amigáveis para mecanismos de
pesquisas (SEFs) em seu componente</a>.*

As rotas do Joomla são criadas e resolvidas pela <a
href="https://docs.joomla.org/index.php?title=JRouter/pt-br&amp;action=edit&amp;redlink=1"
class="new" title="JRouter/pt-br (page does not exist)">classe
JRouter</a>. Esta classe procura na raiz do componente atualmente ativo
(especificado no parâmetro `option` na string de consulta) e inclui o
arquivo `router.php` no diretório raiz desse componente. Em seguida, ele
chama uma das duas funções: uma para criar o localizador uniforme de
recursos (URLs) amigável para mecanismos de pesquisas (SEF) e outra para
interpretar o localizador uniforme de recursos (URLs) amigável para
mecanismos de pesquisas (SEF).

A classe JRouter é substituída pelo S.G.M. (CMS) do Joomla em
`/includes/router.php`. Neste arquivo, as funções de construção e
análise são substituídas para construir e analisar corretamente os
localizadores uniformes de recursos (URLs) para o S.G.M. (CMS) Joomla.

O arquivo `router.php` em cada componente (por exemplo,
`/components/com_content/router.php`) deve conter as duas funções a
seguir:

- ContentBuildRoute - isso cria os localizadores uniformes de recursos
  (URLs) amigáveis para mecanismos de pesquisas (SEFs)
  - Parâmetros
    - \$query - este é um arranjo nomeado contendo as variáveis da(s)
      string(s) de consulta(s)
  - Retorno: posteriormente combinado para criar os localizadores
    uniformes de recursos (URLs) reais (os itens no arranjo não devem
    conter o caractere "/")
- ContentParseRoute - isso interpreta os localizadores uniformes de
  recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs)
  - Parâmetros
    - \$segments - este é um arranjo que contém os segmentos dos
      localizadores uniformes de recursos (URLs) amigáveis para
      mecanismos de pesquisas (SEFs) solicitados.
  - Retorno: um nome =\> arranjo de valores das variáveis da(s)
    string(s) de consulta(s) que o link mapeia

### O plug-in SEF

O plugin *Sistema - SEF* do Joomla herda `JPlugin` e implementa a função
`onAfterRender()`. Nesta função o corpo da resposta que será enviada ao
navegador é recuperado usando `JResponse::getBody()`. O corpo da
resposta é então pesquisado por links contendo `/index.php...` e os
substitui por um localizador uniforme de recursos (URL) amigável para os
mecanismos de pesquisas (SEF) correto chamando `JRoute::_(`*`url`*`)`.

JRoute constrói localizadores uniformes de recursos (URLs) amigáveis
para mecanismos de pesquisas (SEFs) instanciando um objeto `JRouter` e
solicitando que ele construa o link correto a partir do localizador
uniforme de recursos (URL) passado.

### Manipulação de localizadores uniformes de recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs)

Por padrão, os localizadores uniformes de recursos (URLs) amigáveis para
mecanismos de pesquisas (SEFs) são tratados pelo objeto `JRouterSite`
(de `/includes/router.php`) e são chamados por uma chamada para
`JApplication::route() ` em index.php. Esta chamada é feita na variável
`$app` que na verdade é uma instância de `JSite` (de
`/includes/application.php`).

`JApplication::route()` tem um resultado não destrutivo no arranjo
`$_GET`. Ou seja, `JApplication::route()` define variáveis em `$_GET`
chamando `JRequest::set()` com o sinalizador de substituição definido
como falso . Assim, se um nome de variável for retornado de
`JRouter::route()` que já está em `$_GET`, ele não colocará esse valor
em `$_GET`. Isso permite o roteamento personalizado.

### Roteamento personalizado

O Joomla permite que você crie seu próprio mecanismo de roteamento. Para
criar este mecanismo você deve ter um plugin que substitua a função
`JPlugin::onAfterInitialise()`. Esta função então analisa o localizador
uniforme de recursos (URL) e cria as variáveis necessárias em `$_GET`
antes que o roteamento padrão do Joomla seja feito.

*Consulte <a
href="https://docs.joomla.org/Creating_a_System_Plugin_to_augment_JRouter"
class="mw-redirect"
title="Creating a System Plugin to augment JRouter">Criando um plugin de
sistema para aumentar o JRouter</a> (apenas em inglês) para um exemplo.*
