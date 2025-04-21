<!-- Filename: Smart_Search_on_large_sites / Display title: Pesquisa Inteligente em Sites Grandes -->

## Indexação do Site

Smart Search funciona criando e mantendo um índice independente de termos de pesquisa em várias tabelas de banco de dados. O problema para sites grandes é que o processo de indexação pode ser bastante pesado em termos de uso de CPU, memória e disco. Mesmo após a construção inicial do índice, atualizações incrementais também podem ser pesadas. A boa notícia é que consultar o índice é uma operação relativamente rápida e leve.

Smart Search é adequado para a maioria dos sites Joomla. No entanto, a busca apresenta desafios particulares para sites grandes. Deve-se lembrar que o Smart Search é uma implementação pura em PHP de um mecanismo de busca e sites particularmente grandes podem se beneficiar mais ao usar um mecanismo de busca independente, como o Solr.

Para usar a Pesquisa Inteligente em um site grande, você provavelmente precisará ajustar algumas das configurações. O que se segue é um conselho geral sobre o que observar e o que tentar ajustar.

## Sempre Use o Indexador CLI

Como o processo inicial de indexação pode demorar muito, é melhor executar o indexador a partir da linha de comando para evitar qualquer problema devido ao tempo limite das sessões do navegador. O indexador de CLI não ultrapassará o tempo limite, independentemente do tempo que levar para finalizar, e ele pode ser facilmente abortado se surgirem problemas. Além disso, mensagens de erro são visíveis com o indexador de CLI, enquanto podem ficar ocultas ao executar a partir do Administrador.

Para usar o CLI, abra um terminal, vá para a pasta cli na raiz do seu site e emita o seguinte comando:

```
php joomla.php finder:index
```

## Agrupamento

O indexador divide o trabalho de indexação em lotes de itens de conteúdo. Por padrão, o tamanho do lote é definido em 50, o que significa que até 50 itens de conteúdo serão indexados por lote. Aumentar o tamanho do lote pode potencialmente tornar o processo de indexação mais rápido, mas utilizará mais memória e possivelmente mais espaço temporário em disco.

## Problemas de Falta de Memória

Se o indexador estiver ficando sem memória, tente fazer os seguintes ajustes um de cada vez até que o problema seja resolvido.

1. Diminua o tamanho do lote. Se você tiver itens de conteúdo particularmente grandes, o indexador pode ficar sem memória até mesmo com um único item de conteúdo, então tente diminuir para 5 inicialmente e, se ainda ficar sem memória, reduza para 1.
2. Se você puder alocar mais memória para o indexador, faça isso. Você pode aumentar a memória alocada para o indexador de linha de comando usando um parâmetro extra na linha de comando. Por exemplo, para aumentar o limite de memória para 256Mb, use o seguinte comando, substituindo *256M* pela quantidade de memória que você pode alocar com segurança para um processo em seu sistema.
```php
    php -d memory_limit=256M joomla.php finder:index
```
3. Tente identificar quais itens de conteúdo estão fazendo o indexador ficar sem memória. Se não for óbvio, você pode tentar desabilitar todos os plugins de Pesquisa Inteligente, exceto um. Executar o indexador com apenas um plugin habilitado por vez deve revelar qual(is) tipo(s) de conteúdo estão causando o problema. Como último recurso, considere dividir alguns itens de conteúdo excepcionalmente grandes em itens separados. Se o problema for com um tipo de conteúdo personalizado, examine o código do plugin e considere indexar menos do conteúdo disponível por item.

## Problemas com Falta de Espaço em Disco

As tabelas de índice de Pesquisa Inteligente podem crescer rapidamente! A tabela *#__finder_links_termsX* contém uma linha por termo/frase por item de conteúdo e um único artigo do Joomla contendo 1000 palavras normalmente resultará em aproximadamente 3000 linhas sendo adicionadas a essas tabelas. Um segundo artigo de tamanho semelhante adicionará um número similar de linhas, mesmo que ambos os artigos contenham as mesmas palavras. Um site com dezenas de milhares de artigos, alguns dos quais podem conter milhares de palavras, provavelmente acabará com essa tabela de mapeamento contendo milhões de linhas. Não é incomum que as tabelas de índice ocupem vários gigabytes de espaço em disco em tais circunstâncias.

O índice tem uma opção para decidir entre precisão da pesquisa e tamanho do índice. Quando você tem "Buscar por frases" ativado nas opções globais do componente, seu índice será maior, mas também permitirá resultados de pesquisa mais precisos. Tê-lo desativado significará um índice muito menor, mas também impossibilitará a pesquisa de frases inteiras.

## Notas

1. Atualmente não há bloqueio de concorrência para evitar que mais de um processo execute o indexador ao mesmo tempo. Isso quase certamente resultará em um índice corrompido. Mesmo alguém salvando alterações em um item de conteúdo enquanto um índice completo está sendo realizado pode potencialmente danificar o índice.

*Traduzido por openai.com*

