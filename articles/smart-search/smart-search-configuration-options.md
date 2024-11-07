<!-- Filename: Smart_Search_configuration_options / Display title: Opções de Busca Inteligente -->

## Sobre Opções

As opções permitem que você gerencie as configurações globais do Smart Search. As configurações de Opções são herdadas pelas visualizações, mas as configurações em um item de menu substituirão as configurações globais.

O painel de Opções está separado em duas partes. Quando você terminar de fazer ajustes, selecione o botão Salvar; caso contrário, selecione o botão Cancelar para descartar quaisquer alterações.

## Opções de Pesquisa

As opções de pesquisa controlam o comportamento dos formulários de pesquisa e dos resultados de pesquisa para o front-end do Finder.

- **Descrição do Resultado** - Esta opção controla se os resultados da pesquisa devem ser exibidos com descrições. O padrão é Mostrar.
- **Tamanho da Descrição** - Esta opção controla o comprimento máximo de caracteres das descrições dos resultados de pesquisa. As descrições são truncadas para o comprimento máximo, mas a truncagem é sempre feita no último caractere de espaço para não interromper uma palavra no meio. Só é efetivo quando a opção Descrição do Resultado está configurada para Mostrar. O padrão é 255 caracteres.
- **URL do Resultado** - Esta opção controla se os resultados da pesquisa devem ser exibidos com URLs abaixo da descrição (se habilitado). O padrão é Mostrar.
- **Pesquisa Avançada** - Esta opção controla se as opções de pesquisa avançada devem ser exibidas. O padrão é Mostrar.
- **Expandir Pesquisa Avançada** - As opções de pesquisa avançada estão contidas em um contêiner expansível. Esta opção controla se o contêiner de opções de pesquisa avançada deve estar expandido por padrão. O padrão é Não.
- **Filtros de Data** - Esta opção controla se os filtros de data devem ser exibidos nas opções de pesquisa avançada. O padrão é Ocultar.
- **Rótulos de Resultado** - Esta opção controla se os resultados da pesquisa devem ser exibidos com Rótulos. Requer que o JXtended Labels esteja instalado. O padrão é Mostrar.
- **Destacar Termos de Pesquisa** - Esta opção controla se os termos de pesquisa devem ser destacados nos resultados da pesquisa. O padrão é Sim.

## Opções de Índice

As opções de índice controlam o comportamento do indexador usado para processar e
analisar o conteúdo para pesquisa. A maioria das configurações, como o multiplicador de peso
e opções de stemmer, não produzirão mudanças imediatas, pois são usadas durante a indexação 
e os efeitos de alterar essas configurações só serão vistos após o índice ter sido 
eliminado e reexecutado.

- **Tamanho do Lote do Indexador** - Esta opção controla o tamanho do lote do indexador.
  O indexador do Smart Search divide o processo total de indexação em vários
  lotes para reduzir a carga do servidor e evitar os limites de memória e tempo de
  execução do PHP. Se os itens de conteúdo a serem indexados forem
  particularmente curtos e/ou o servidor for particularmente rápido, o indexador
  pode processar mais itens por lote. No entanto, se os itens de conteúdo
  a serem indexados forem particularmente longos e/ou o servidor for
  particularmente lento, o indexador terá que processar menos itens por lote.
  O padrão é 50.
- **Limite da Tabela de Memória** - Esta opção controla o limite da tabela de memória.
  O indexador do Smart Search utiliza tabelas de memória MySQL para armazenar
  temporariamente dados de conteúdo em vez de armazenar os dados nos buffers de
  memória do PHP, porque itens de conteúdo grandes rapidamente esgotarão as
  configurações padrão de limite de memória do PHP. No entanto, tabelas de
  memória MySQL também têm limites de tamanho ajustáveis e reajustá-los não é
  confiável. Esta configuração é fornecida para lidar com tabelas de memória com
  limites de tamanho menores que o usual e só deve ser ajustada quando erros de
  Tabela Cheia ocorrerem durante a indexação. O padrão é 30.000. Se você
  encontrar erros de "tabela cheia", tente **reduzir** este parâmetro. O valor
  ideal deve resultar em tabelas de memória que são um pouco menores que o
  parâmetro <a
  href="http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_max_heap_table_size"
  rel="nofollow noreferrer noopener"><em>max_heap_table_size</em></a> no MySQL,
  que por padrão é 16 megabytes.
- **Multiplicador de Peso do Texto do Título** - Esta opção controla o quanto
  a influência do texto do título tem na pontuação de relevância geral de um
  resultado de busca. O padrão é 1.7.
- **Multiplicador de Peso do Texto do Corpo** - Esta opção controla o quanto
  a influência do texto do corpo tem na pontuação de relevância geral de um
  resultado de busca. O padrão é 0.7.
- **Multiplicador de Peso dos Metadados** - Esta opção controla o quanto
  a influência do texto dos metadados tem na pontuação de relevância geral de
  um resultado de busca. O padrão é 1.2.
- **Multiplicador de Peso do Texto do Caminho** - Esta opção controla o quanto
  a influência do texto do caminho/URL tem na pontuação de relevância geral de um
  resultado de busca. O padrão é 2.0.
- **Multiplicador de Peso do Texto Diverso** - Esta opção controla o quanto
  a influência do texto diverso tem na pontuação de relevância geral de um
  resultado de busca. O padrão é 0.3.
- **Stemmer** - Esta opção controla qual stemmer de linguagem deve ser
  usado durante a indexação. O stemmer Apenas Inglês é uma implementação 
  pura em PHP que não tem dependências. O stemmer Snowball 
  requer a extensão Stem PHP, mas oferece suporte a 14 idiomas, incluindo 
  dinamarquês, alemão, inglês, espanhol, finlandês, francês, húngaro, italiano,
  norueguês, holandês, português, romeno, russo e turco. O padrão é Apenas
  Inglês.
- **Habilitar Registro** - cria um arquivo de log durante o processo de 
  indexação. O padrão é não.

*Traduzido por openai.com*

