<!-- Filename: Using_A_Sitemap / Display title: Usando um mapa de sites -->

## Usando um mapa de sites

Embora os mecanismos de pesquisa geralmente possam encontrar suas
páginas pela maneira como estão vinculadas a outros lugares na Internet,
é uma boa prática criar um mapa de site que forneça aos "bots" dos
mecanismos de pesquisa uma lista das páginas em seu site - pense nisso
como um mapa para encontrar todo o conteúdo do seu site.  
Os mapas de site não são apenas importantes para os mecanismos de
pesquisa, mas também são muito úteis para pessoas com deficiências que
podem precisar de uma interface simples para visualizar a estrutura do
site e navegar pelo site sem usar as estruturas do menu.
<a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Nota do grupo de trabalho W3C sobre
mapas de sites</a>  

Um mapa de site serve a vários propósitos:

- Fornece uma lista estruturada mostrando uma visão geral de todo o
  conteúdo de seu site;
- permite que um visitante obtenha rapidamente uma visão geral da
  estrutura de seu site;
- fornece uma maneira alternativa de navegar em seu site, sem a
  necessidade de estruturas de menu complexas;
- fornece aos mecanismos de pesquisa um meio de encontrar conteúdo que
  pode não estar disponível por meio de suas estruturas de menu (por
  exemplo, páginas de destino).

### Tipos de mapas de sites

É possível fornecer mapas de sites para tipos específicos de
informações, incluindo:

- Vídeo <a
  href="https://developers.google.com/search/docs/advanced/sitemaps/video-sitemaps?visit_id=637845456253725889-2649158247&amp;rd=1#guidelines-for-video-sitemaps"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Ajuda do Google sobre mapas de sites
  de vídeos</a>
- Imagens <a
  href="https://developers.google.com/search/docs/advanced/sitemaps/image-sitemaps?visit_id=637845457605356615-3074991136&amp;rd=1"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Ajuda do Google sobre mapas de sites
  de imagens</a>
- Notícias <a
  href="https://developers.google.com/search/docs/advanced/sitemaps/news-sitemap?visit_id=637845468852694381-144480659&amp;rd=3"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Ajuda do Google sobre mapas de sites
  de notícias</a>
- Internacional <a
  href="https://developers.google.com/search/docs/advanced/crawling/localized-versions?ref_topic=2370587&amp;visit_id=637845467776240401-3867996884&amp;rd=2"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Ajuda do Google sobre mapas de sites
  internacionais</a>

Esses mapas de sites especializados permitem que você forneça
informações relacionadas ao tipo de mídia específico - por exemplo, com
um mapa de sites de vídeos, você pode fornecer informações sobre os
tempos de execução, categorias e status familiar; com os mapas de sites
de imagens, você pode especificar os assuntos das imagens, suas licenças
de uso e os tipos de imagens.

### Criando um mapa de sites

Em um site estático, criar um mapa do sites é simplesmente criar
manualmente um arquivo xml usando os padrões apropriados e salvá-lo como
um arquivo xml. Em um site dinâmico, onde o conteúdo muda regularmente,
isso não é realmente uma opção - você teria que atualizar manualmente o
arquivo de mapa de site toda vez que adicionasse algum conteúdo novo!

Por esta razão, existem várias extensões de mapas de sites disponíveis
no diretório de extensões do Joomla (<a
href="https://extensions.joomla.org/category/structure-a-navigation/site-map"
class="external text" target="_blank"
rel="noreferrer noopener">categoria mapas de sites no diretório de
extensões do Joomla</a>) que permitem que você dinamicamente construa um
mapa de site que atenda aos padrões de mapas de sites esperados pelos
mecanismos de pesquisa.
<a href="https://www.sitemaps.org/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">Protocolo de mapas de
sites</a>

A maioria dessas extensões funciona escolhendo itens de menu que você
deseja incluir em um mapa de sites e especificando com que frequência
eles mudam (consulte Frequência de atualização). Também é possível
incluir subpáginas desses itens de menu (por exemplo, um item de menu
pode levar a uma página de blog de categoria, mas você deseja exibir
todos os artigos mostrados nesta página como itens individuais - outro
exemplo pode ser um item de menu apontando para uma página de categoria
de loja e, no mapa do sites, você deseja listar a categoria e, em
seguida, cada produto dentro dela como um link separado).

### Frequência de atualização

Embora você possa especificar manualmente em seu mapas de sites com que
frequência os spiders do mecanismo de pesquisa devem visitar seu site, a
maioria dos mecanismos de pesquisa possui sistemas integrados que
ajustam automaticamente a frequência de visitas de retorno com base na
frequência com que a página em questão foi alterada.

Assim, por exemplo, se você disser aos bots dos mecanismos de pesquisa
para visitar sua página diariamente, mas quando eles visitarem a página,
nada mudou por uma semana, ele poderá ajustar a frequência de revisitas
de acordo e não retornar com a frequência que você disse. Você pode
solicitar, através dos vários portais de webmasters, que a taxa de
revisita seja alterada, se necessário.

Isso sugere, portanto, que, se você alterar o conteúdo regularmente, seu
site será "spiderado" com mais frequência - levando o conteúdo a ser
indexado mais rapidamente do que sites que não mudam com frequência.

Geralmente, é sensato especificar páginas que são estáticas para serem
rastreadas com menos frequência do que aquelas que mudam regularmente.
Por exemplo, um artigo de texto estático pode ser definido com uma
frequência de atualização de uma vez por mês, enquanto seu blog ou
página de notícias pode ser definido com uma frequência de atualização
de uma vez por dia ou uma vez por semana, dependendo da frequência com
que você adiciona novo conteúdo.

### Mapas de sites em html

Um mapa de sites html é essencialmente uma tabela de conteúdo para o seu
site que você pode disponibilizar aos visitantes do seu site. Isso serve
para três propósitos:

1.  Ele fornece um local onde os visitantes podem acessar facilmente
    qualquer conteúdo em seu site, mesmo que não seja necessariamente
    fácil de acessar por outros auxílios de navegação no site;
2.  fornece um armazenamento centralizado de links para o conteúdo do
    seu site que pode ser facilmente indexado pelos mecanismos de
    pesquisa;
3.  permite que usuários com deficiências possam navegar rapidamente em
    seu site com uma lista simples de links, em vez de menus complexos.

No mínimo, um mapa de site deve ter um link para as principais seções e
páginas de seu site, mas quanto mais detalhado você puder torná-lo,
melhor.

Existem extensões disponíveis mencionadas anteriormente que criam mapas
de sites automaticamente com base no conteúdo do Joomla.

### Mapas de sites em xml

Os mapas de site em xml são uma maneira fácil para os webmasters
informarem os mecanismos de pesquisa sobre páginas novas e existentes em
seus sites que estão disponíveis para rastreamento. Na sua forma mais
simples, um mapa de sites é um arquivo xml que lista as urls de um site
junto com metadados adicionais sobre cada url (quando foi atualizado
pela última vez, com que frequência muda e quão importante é, em relação
a outras urls no site ) para que os mecanismos de pesquisa possam
rastrear o site de maneira mais inteligente.

O uso do protocolo de mapas de sites não garante que as páginas web
sejam incluídas nos mecanismos de pesquisas, mas fornece dicas para que
os rastreadores da web façam um trabalho melhor ao rastrear seu site.

1.  Um mapa de sites em xml fornece uma lista de links para o conteúdo
    de seu site que pode ser facilmente indexado pelos mecanismos de
    pesquisas;
2.  é possível criar mapas de sites em xml específicos para notícias,
    urls móveis, imagens e vídeos.

Existem extensões disponíveis que criam mapas de sites em xml
automaticamente com base no conteúdo do Joomla.
