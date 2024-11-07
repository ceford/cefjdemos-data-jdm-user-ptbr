<!-- Filename: Using_A_Sitemap / Display title: Usando um Sitemap  -->

## Usando um Sitemap

Embora os motores de busca geralmente possam encontrar suas páginas pela forma como elas são vinculadas a outros lugares na internet, é uma boa prática criar um Sitemap que forneça aos robôs dos motores de busca uma lista das páginas do seu site - pense nele como um mapa para encontrar todo o conteúdo do seu site. Os Sitemaps não são importantes apenas para os motores de busca, mas também são muito úteis para pessoas com deficiência que possam precisar de uma interface simples para visualizar a estrutura do seu site e navegar sem o uso das suas estruturas de menu. <a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html" rel="nofollow noreferrer noopener">Nota do Grupo de Trabalho da W3C sobre Sitemaps</a>

Um sitemap serve a vários propósitos:

- Fornece uma lista estruturada mostrando uma visão geral de todo o conteúdo do seu site
- Permite que um visitante rapidamente obtenha uma visão geral da estrutura do seu site
- Oferece um meio alternativo de navegar pelo seu site, sem a necessidade de estruturas de menu complexas
- Fornece aos motores de busca um meio de encontrar conteúdo que pode não estar disponível através das suas estruturas de menu (por exemplo, páginas de destino)

### Tipos de Sitemap

É possível fornecer sitemaps para tipos específicos de informação, incluindo:

- Vídeo <a href="https://support.google.com/webmasters/answer/80471" rel="nofollow noreferrer noopener">Ajuda do Google sobre sitemaps de vídeo</a>
- Imagens <a href="https://support.google.com/webmasters/answer/178636" rel="nofollow noreferrer noopener">Ajuda do Google sobre sitemaps de imagem</a>
- Notícias <a href="https://support.google.com/news/publisher/answer/75717" rel="nofollow noreferrer noopener">Ajuda do Google sobre sitemaps de notícias</a>
- Internacional <a href="https://support.google.com/webmasters/answer/2620865?hl=pt-BR&amp;ref_topic=2370587" rel="nofollow noreferrer noopener">Ajuda do Google sobre sitemaps internacionais</a>

Esses sitemaps especializados permitem que você forneça informações relacionadas ao tipo específico de mídia - por exemplo, com um sitemap de vídeo, você pode fornecer informações sobre o tempo de execução, categoria e status de adequação para a família; com sitemaps de imagem, você pode especificar o assunto da imagem, sua licença de uso e tipo de imagem.

### Criando um sitemap

Em um site estático, criar um sitemap é simplesmente uma questão de criar manualmente um arquivo XML usando os padrões apropriados e salvá-lo como um arquivo XML. Em um site dinâmico, onde o conteúdo muda regularmente, isso não é realmente uma opção - você teria que atualizar manualmente o arquivo do sitemap toda vez que adicionasse algum conteúdo novo!

Por essa razão, existem várias extensões de sitemap disponíveis no Diretório de Extensões do Joomla (<a href="https://extensions.joomla.org/category/structure-a-navigation/site-map" rel="noreferrer noopener">Categoria de Sitemap no Diretório de Extensões do Joomla</a>), que permitem que você construa dinamicamente um sitemap que atenda aos padrões de sitemap esperados pelos motores de busca.
<a href="https://www.sitemaps.org/" rel="nofollow noreferrer noopener">Protocolo de Sitemaps</a>

A maioria dessas extensões funciona escolhendo os itens de menu que você deseja incluir em um sitemap e especificando com que frequência eles mudam (veja Frequência de Atualização). Também é possível incluir sub-páginas desses itens de menu (por exemplo, um item de menu pode levar a uma página de blog por categoria, mas você quer exibir todos os artigos que são mostrados nessa página como itens individuais - outro exemplo pode ser um item de menu apontando para uma página de categoria de loja, e no sitemap você pode querer listar a categoria, e então cada produto dentro dela como um link separado).

### Frequência de Atualização

Embora você possa especificar manualmente no seu Sitemap com que frequência os robôs dos motores de busca devem visitar seu site, a maioria dos motores de busca possui sistemas embutidos que ajustam automaticamente a frequência de visitas de retorno com base em quão frequentemente a página em questão foi alterada.

Então, por exemplo, se você disser aos robôs dos motores de busca para visitar sua página diariamente, mas quando ele visitar a página nada tiver mudado por uma semana, ele pode ajustar a frequência de revisitas de acordo e não voltar tão frequentemente quanto você disse. Você pode solicitar, através dos vários portais de webmasters, que a taxa de revisita seja alterada se necessário.

Isso sugere, portanto, que se você tem conteúdo que muda regularmente, seu site será 'varrido' mais frequentemente - levando a que o conteúdo seja indexado mais rapidamente do que em sites que não mudam com frequência.

Geralmente é sensato especificar que páginas estáticas sejam rastreadas com menos frequência do que aquelas que mudam regularmente. Por exemplo, um artigo de texto estático pode ser configurado com uma frequência de atualização de uma vez por mês, enquanto sua página de blog ou de notícias pode ser configurada com uma frequência de atualização de uma vez por dia ou uma vez por semana, dependendo de quão frequentemente você adiciona novo conteúdo.

### Sitemaps em HTML

Um sitemap em HTML é essencialmente um índice do seu site que você pode disponibilizar aos visitantes do seu site. Isso serve a dois propósitos:

1.  Ele fornece um lugar onde os visitantes podem ir para acessar facilmente qualquer conteúdo do seu site, mesmo que não seja necessariamente fácil de acessar por outros meios de navegação no site.
2.  Ele fornece um armazenamento centralizado de links para o conteúdo do seu site que pode ser facilmente indexado por motores de busca.
3.  Ele permite que usuários com deficiência possam navegar rapidamente pelo seu site com uma lista simples de links, ao invés de menus complexos.

No mínimo, um sitemap deve vincular às principais seções e páginas do seu site, mas quanto mais detalhado você puder fazê-lo, melhor.

Existem extensões disponíveis mencionadas anteriormente que criam sitemaps automaticamente com base no conteúdo do Joomla.

### Sitemaps em XML

Os sitemaps em XML são uma maneira fácil para webmasters informarem aos motores de busca sobre páginas novas e existentes em seus sites que estão disponíveis para rastreamento. Na sua forma mais simples, um Sitemap é um arquivo XML que lista URLs para um site juntamente com metadados adicionais sobre cada URL (quando foi atualizado pela última vez, com que frequência geralmente muda, e quão importante é em relação a outras URLs no site) para que os motores de busca possam rastrear o site de maneira mais inteligente.

Usar o protocolo de Sitemap não garante que as páginas da web sejam incluídas nos motores de busca, mas fornece dicas para que as ferramentas de rastreamento façam um trabalho melhor de varredura no seu site.

1.  Um sitemap em XML fornece uma lista de links para o conteúdo do seu site que pode ser facilmente indexado pelos motores de busca.
2.  É possível criar sitemaps específicos em XML para Notícias, URLs Móveis, Imagens e Vídeo.

Existem extensões disponíveis que criam sitemaps em XML automaticamente com base no conteúdo do Joomla.

*Traduzido por openai.com*

