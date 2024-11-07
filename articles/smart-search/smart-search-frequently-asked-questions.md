<!-- Filename: Smart_Search_Frequently_Asked_Questions / Display title: Perguntas Frequentes sobre Busca Inteligente  -->

## Por que devo usar a Pesquisa Inteligente?

A tecnologia de busca melhorou consideravelmente ao longo dos anos desde que o Joomla foi lançado e, no entanto, o componente de busca padrão e básico não mudou muito nesse tempo. Ainda é muito rudimentar e carece do tipo de funcionalidades de busca que os usuários da web passaram a esperar, especialmente dada a prevalência de mecanismos de busca avançados, como o Google. A Pesquisa Inteligente permite incorporar algumas dessas características de busca mais avançadas ao seu site.

## Por que Criar um Plugin de Pesquisa Inteligente?

Geralmente, se você tem um tipo de conteúdo que não é gerenciado pelos componentes principais do Joomla, e você deseja dar aos visitantes do seu site a oportunidade de pesquisar esse conteúdo, você precisará escrever um Plugin de Pesquisa Inteligente para suportá-lo. Por exemplo, suponha que você tenha um componente que armazena informações sobre diferentes espécies de animais. O componente mantém uma tabela de banco de dados contendo campos como nome científico, nome vulgar, classificação e uma descrição. Então, você precisará criar um Plugin que informará ao indexador de Pesquisa Inteligente como indexar os dados nessa tabela. Além de indexar palavras e frases individuais, você também pode fazer com que o Plugin adicione cada registro a um mapa de conteúdo, que neste caso pode incluir as <a href="https://pt.wikipedia.org/wiki/Taxonomia_(biologia)" rel="nofollow noreferrer noopener">classificações biológicas de reino, filo, classe, ordem e família</a>. Mapas de conteúdo podem então ser usados para filtrar os resultados da pesquisa.

## É possível selecionar vários nós nos menus suspensos de filtro?

Sim, isso é totalmente suportado pelo próprio Smart Search. De fato, você pode usar qualquer interface de usuário que quiser criar para os filtros. Basta dar uma olhada no código fornecido no módulo e componente padrão do Frontend e você verá como deve fazer isso.

## Eu Tenho um Site Grande. Posso Usar o Smart Search?

Sites grandes podem se beneficiar mais de um mecanismo de busca dedicado e independente, como o Solr, em vez da implementação puramente em PHP usada no Smart Search. Nesta primeira iteração da busca avançada no Joomla, é provável que surjam questões relacionadas à escalabilidade e desempenho. Também há potencial para ocorrerem condições de corrida ao atualizar o índice em mudanças frequentes de conteúdo. Espera-se que essas questões sejam abordadas de forma mais completa em uma versão futura do Joomla.

## Por que a Pesquisa Inteligente tem tantas tabelas?

A Pesquisa Inteligente adiciona várias novas tabelas a uma instalação do Joomla, incluindo 16 "tabelas de mapeamento". Essas tabelas de mapeamento resolvem a relação de muitos-para-muitos entre os termos de pesquisa e os itens de conteúdo que os contêm. Em teoria, essas 16 tabelas poderiam ser mescladas em uma única tabela, e fazer isso teria um impacto insignificante em sites pequenos. No entanto, em sites maiores, haveria um impacto substancial no desempenho, porque a tabela de mapeamento teria um número muito grande de entradas, e atualizar uma tabela tão grande pode ser demorado.

## Por que a Pesquisa Inteligente Usa Tanto Espaço em Disco?

Manter um índice de termos de pesquisa requer uma quantidade considerável de espaço em disco, que aumenta conforme o número de termos contidos nos itens de conteúdo. Como frases também são indexadas, quanto mais longas as frases, mais espaço em disco é necessário. Para a Pesquisa Inteligente no Joomla 2.5, o comprimento máximo de uma frase foi fixado em 3 termos como um compromisso razoável entre a usabilidade da pesquisa e o uso de espaço em disco. É provável que isso se torne um parâmetro ajustável em uma versão futura da Pesquisa Inteligente.

## Por que as entradas nas tabelas de mapeamento não são distribuídas uniformemente?

Talvez seja surpreendente que o número de entradas em cada uma das tabelas de mapeamento não seja nem mesmo aproximadamente o mesmo. Certamente o desempenho seria melhor com uma distribuição uniforme? Na verdade, não, há um equilíbrio entre o desempenho de inserção e o desempenho de busca, sendo a distribuição uniforme boa para o primeiro, mas ruim para o último. Esta é uma área de pesquisa contínua com o número de tabelas e o algoritmo de distribuição sujeitos a mudanças à luz da experiência.

## Por que Existe um Plugin de Conteúdo de Pesquisa Inteligente Separado?

Esta é apenas uma conveniência que facilita a habilitação ou desabilitação de todos os Plugins de Pesquisa Inteligente com uma única operação. Isso foi considerado desejável porque a Pesquisa Inteligente não está ativada por padrão no Joomla 2.5.

## Por que os plugins de pesquisa inteligente usam eventos separados, como *onFinderContentAfterSave*?

A Pesquisa Inteligente usa seus próprios eventos, como onFinderContentAfterSave, em vez do equivalente genérico onContentAfterSave, puramente como uma conveniência para facilitar a ativação ou desativação da indexação da Pesquisa Inteligente ao habilitar/desabilitar um único plugin.

## Por que a Pesquisa Inteligente Não Está Ativada por Padrão no Joomla 2.5 e Joomla 3.x?

Como o Joomla 2.5 é o último da série 1.x/2.x, ele deve manter um alto grau de compatibilidade retroativa com a versão anterior da série. Como a Pesquisa Inteligente é algo totalmente novo e não tem nenhuma semelhança com o componente de busca regular desta ou de lançamentos anteriores, considerou-se importante que os usuários que fazem a atualização a partir dessas versões anteriores não fossem obrigados a mudar a forma como a busca funciona em seus sites. De fato, a ativação da Pesquisa Inteligente é algo que deve ser feito de maneira cuidadosamente planejada.

## Por que Não Há uma API de Busca?

O foco da versão atual do Smart Search foi transferir o código do antigo componente JXtended Finder para a versão mais recente do Joomla. Como esse código já era considerado estável e havia apenas uma pequena janela de oportunidade para portá-lo, acreditou-se que um grande redesenvolvimento do Finder estava fora do escopo para o lançamento do Joomla 2.5. Consequentemente, o código utiliza Plugins para evitar quaisquer alterações no código principal do CMS, em vez de desenvolver uma API de busca adequada. Planejamos criar uma API desse tipo para uma futura iteração do Joomla.  

## A Pesquisa Inteligente Pode Realizar Pesquisa com Facetas?

Sim. A pesquisa avançada disponível na página de resultados de busca e o módulo de pesquisa inteligente fornecem um exemplo de como você pode filtrar os resultados de pesquisa para produzir uma pesquisa com facetas. Nada impede que você crie suas próprias variações sobre essas ideias básicas. Por exemplo, você poderia alterar os menus suspensos simples para aceitar seleções múltiplas, ou poderia substituir os menus suspensos por uma matriz de caixas de seleção.

## Por Que Pesquisas com Curingas Não São Suportadas?

A antiga busca do Joomla utilizava um método de pesquisa muito primitivo, que dependia da busca FULLTEXT fornecida pelo banco de dados. Isso era muito ineficiente, mas oferecia um meio simples de lidar com consultas de busca usando curingas. A Pesquisa Inteligente oferece um recurso de autocompletar que é, efetivamente, uma busca com curingas dos termos no índice, mas a busca completa com curingas não é suportada devido ao potencial de sobrecarregar o servidor caso a funcionalidade fosse abusada. Na maioria dos casos, as buscas com curingas são usadas para lidar com variações em um termo de busca. Por exemplo, buscar por *malabar\** para captar referências a *malabarismo* assim como *malabarista*. A Pesquisa Inteligente tenta evitar a necessidade de buscas com curingas, ao invés disso, suportando a derivação de palavras, onde palavras que têm a mesma raiz são consideradas equivalentes, de modo que buscar por *malabarista* também recupere instâncias de *malabarismo* sem a necessidade de usar curingas.

## O Smart Search pode ser usado em sites multilíngues?

Sim, mas ainda existem alguns problemas a serem resolvidos, especialmente no que diz respeito ao suporte para idiomas asiáticos.

- Para ser indexado corretamente, você deve garantir que todo o conteúdo seja um UTF-8 válido.
- O recurso *Você quis dizer?* usa a função Soundex para encontrar frases de busca foneticamente similares. No entanto, o Soundex não funciona bem para idiomas que não sejam o inglês e, para muitos idiomas, não funciona de forma alguma. Atualmente, estamos pesquisando métodos alternativos para oferecer esse recurso.

Se você usar o Smart Search em um site multilíngue e encontrar algum problema, por favor, relate-o no rastreador para que possamos compreender melhor os problemas que precisam ser resolvidos.

## Os plugins *jXTended* Finder funcionarão com o Smart Search?

Não. Você precisará atualizar os plugins Finder para que funcionem com o Smart Search. No entanto, as alterações não devem ser difíceis de implementar e, na maioria dos casos, resultarão em um código significativamente menor. Se você der uma olhada nos plugins atuais do Smart Search, verá que atualizar um plugin Finder é bastante simples.

*Traduzido por openai.com*

