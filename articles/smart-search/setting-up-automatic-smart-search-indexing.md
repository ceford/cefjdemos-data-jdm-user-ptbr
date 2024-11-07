<!-- Filename: Setting_up_automatic_Smart_Search_indexing / Display title: Indexação de Busca Inteligente -->

## Indexação Automática

Embora o índice de Busca Inteligente seja mantido atualizado automaticamente sempre que itens de conteúdo são alterados, há algumas circunstâncias em que você precisa executar o indexador novamente. Você pode fazer isso manualmente usando o botão de ferramenta Indexar na página Busca Inteligente: Conteúdo Indexado. No entanto, se você precisa reindexar conteúdo automaticamente, é possível executar o indexador a partir da linha de comando. Isso torna particularmente conveniente executar o indexador a partir de um trabalho *cron*.

No diretório CLI, a linha de comando é:

```
php joomla.php finder:index
```

A saída típica do indexador de linha de comando se parece com isto:

    INDEXADOR DE BUSCA INTELIGENTE
    ============================

    Iniciando o Indexador
    Configurando plugins do Finder
    Configurado 154 itens em 0,094 segundos.
     * Processado lote 1 em 0,213 segundos.
     * Processado lote 2 em 0,182 segundos.
     * Processado lote 3 em 0,177 segundos.
     * Processado lote 4 em 0,009 segundos.
    Tempo Total de Processamento: 0,676 segundos.

## Expurgar Antes de Indexar

Normalmente, executar o indexador fará uma atualização incremental do índice. Ou seja, ele atualizará apenas o índice para aqueles itens de conteúdo que foram alterados desde a última atualização do índice. No entanto, se você precisar limpar completamente todas as entradas existentes do índice antes de reconstruí-lo completamente, então você precisará realizar uma operação de "expurgar e depois indexar". Para fazer isso, você pode adicionar o argumento `--purge` na linha de comando, assim:

```bash
php joomla.php finder:index --purge
```

Observe que isso tentará preservar quaisquer filtros estáticos que você possa ter configurado, enquanto clicar no botão "Purgar" na barra de ferramentas do Administrador **não** preservará seus filtros estáticos.

## Configurando uma Tarefa *cron*

Embora os detalhes específicos estejam além do escopo deste artigo, em geral, você apenas precisará inserir o comando acima no gerenciador de tarefas *cron* e especificar o(s) horário(s) em que a tarefa deve ser executada. Você provavelmente precisará incluir o caminho completo para o indexador. Por exemplo, assim:

    php /var/www/myjoomla/cli/joomla.php finder:index -- purge

E possivelmente o caminho completo para o arquivo php, como `/usr/local/opt/php@8.2/bin/php`.

## Problemas de Falta de Memória

Se o seu site tiver requisitos de indexação particularmente complexos, é possível que a alocação de memória padrão não seja suficiente para que o indexador execute até a conclusão. Você pode aumentar a memória alocada para o indexador de linha de comando usando um parâmetro extra na linha de comando, assim:

```php
php -d memory_limit=256M joomla.php finder:index
```

Substitua `256M` pelo valor que for apropriado para suas circunstâncias.

O indexador de linha de comando usa os mesmos parâmetros que o indexador na página de Conteúdo Indexado da Pesquisa Inteligente. Você pode alterar os parâmetros usando o botão de opções na barra de ferramentas dessa página. Note que tanto o campo **Tamanho do Lote do Indexador** quanto o **Limite de Memória da Tabela** afetam a quantidade de memória usada pelo indexador.

*Traduzido por openai.com*  

