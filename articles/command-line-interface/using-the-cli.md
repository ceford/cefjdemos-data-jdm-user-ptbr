<!-- Filename: J4.x:Using_the_CLI / Display title: Usando a CLI  -->

## A Interface de Linha de Comando (CLI)

Se você tiver acesso ao terminal do servidor que executa seu site, pode usar a CLI do Joomla para realizar tarefas rotineiras sem a necessidade de usar credenciais de login do usuário do Joomla. Mesmo sem acesso ao terminal, como em algumas contas de hospedagem compartilhada, você pode executar comandos CLI usando trabalhos cron. Comandos CLI costumam ser mais rápidos ou mais convenientes do que seus equivalentes realizados através da interface do Administrador do Joomla (ou cPanel). Backup do site e configuração do site para offline/online são exemplos de onde você pode preferir usar a CLI.

O núcleo do Joomla possui cerca de 30 comandos úteis, e você pode adicionar mais com extensões adicionais. Por exemplo, você poderia buscar dados externos como Geolocalização ou dados de taxa de câmbio para um componente personalizado.   

## Usando o CLI

O CLI é utilizado invocando o executável de linha de comando do PHP. Isso geralmente é diferente daquele usado por um servidor web, como o Apache. Se você estiver usando um trabalho cron, talvez precise fornecer o caminho completo para o executável PHP, assim:

    /usr/local/bin/php /home/nomeusuario/public_html/[subpasta opcional]/cli/joomla.php

Caso contrário, ao usar a linha de comando do terminal, mude o diretório para a pasta CLI do Joomla e comece a executar o comando sem parâmetros:

    cd /home/nomeusuario/public_html/[subpasta opcional]/cli
    php joomla.php

![Lista de comandos](../../../en/images/command-line-interface/cli-command-list.png)

E experimente alguns comandos de ajuda para se familiarizar com o que esperar:

    php joomla.php help
    php joomla.php list
    php joomla.php help cache:clean
    php joomla.php help config:get

Cada uma das descrições de ajuda e strings de utilização são codificadas nos arquivos da biblioteca Console ou em plugins de terceiros.

Experimente alguns comandos de ação simples:

    php joomla.php config:get debug
    php joomla.php cache:clean
    php joomla.php site:down
    php joomla.php site:up

## Opções

Se você estiver chamando comandos a partir de um cron, talvez não deseje ver nenhuma saída:

    php joomla.php -q cache:clean

Observe que as opções podem usar um espaço ou sinal de =, mas as variáveis devem usar um sinal de =:

    php joomla.php session:gc --application administrator
    php joomla.php session:gc --application=administrator

    php joomla.php config:set debug=true

## Comandos

Uma breve explicação de cada comando principal.

### Cache

Limpar entradas expiradas do cache do sistema:

```shell
php joomla.php cache:clean --help
php joomla.php cache:clean
```

![Saída do cache clean](../../../en/images/command-line-interface/cli-cache-clean.png)

```shell
php joomla.php cache:clean expired
```

![Saída do cache clean expired](../../../en/images/command-line-interface/cli-cache-clean-expired.png)

### Config

Obter ou definir uma variável de configuração, uma das variáveis em configuration.php ou um grupo de variáveis. Grupos válidos são db, session, mail,

```shell
php joomla.php config:get debug --help
php joomla.php config:get debug
```

![Saída do config get debug](../../../en/images/command-line-interface/cli-get-debug.png)

```shell
php joomla.php config:set debug=true
```

![Saída do config set debug](../../../en/images/command-line-interface/cli-set-debug.png)

```shell
php joomla.php config:get --group session
```

![Saída do config get group session](../../../en/images/command-line-interface/cli-config-get-group-session.png)

### Core

Verificar atualizações ou atualizar o Joomla.

```shell
php joomla.php core:check-updates --help
php joomla.php core:check-updates
```

![Saída do core check updates](../../../en/images/command-line-interface/cli-check-updates.png)

```shell
php joomla.php core:update --help
php joomla.php core:update
```

![Saída do core update](../../../en/images/command-line-interface/cli-core-update.png)

### Banco de Dados

Exportar ou Importar o banco de dados. Você pode exportar ou importar todas as tabelas ou uma tabela selecionada. Não use este recurso para importar todas as tabelas de um site multilíngue. Existe um problema que pode parar o funcionamento do Smart Search completamente.

```shell
php joomla.php database:export --help
php joomla.php database:export --table f4rc2_banners --folder /home/username/tmp/mydb (uma tabela)
php joomla.php database:export --folder /home/username/tmp/mydb (todas as tabelas)
```

```shell
php joomla.php database:import --help
php joomla.php database:import --table /home/username/tmp/mydb/f4rc2_banners (uma tabela)
[ERRO] O arquivo /home/username/tmp/mydb/f4rc2_banners.xml não existe.
php joomla.php database:import --folder /home/username/tmp/mydb (todas as tabelas nesta pasta)
```

### Extensão

Listar, Descobrir, Instalar ou Remover extensões.

```shell
php joomla.php extension:list --help
php joomla.php extension:list
php joomla.php extension:list --type component
php joomla.php extension:list --type file
php joomla.php extension:list --type language
php joomla.php extension:list --type library
php joomla.php extension:list --type module
php joomla.php extension:list --type package
php joomla.php extension:list --type plugin
php joomla.php extension:list --type template
```

```shell
php joomla.php extension:discover --help
php joomla.php extension:discover
php joomla.php extension:discover:list
php joomla.php extension:discover:install --eid=
```

```shell
php joomla.php extension:install --help
php joomla.php extension:install --path=
php joomla.php extension:install --url=
```

```shell
php joomla.php extension:remove --help
php joomla.php extension:remove
```

### Finder

Limpa e reconstrói o índice (filtros de pesquisa são preservados).

```shell
php joomla.php finder:index --help
php joomla.php finder:index
php joomla.php finder:index purge
```

![Saída do finder index purge](../../../en/images/command-line-interface/cli-finder-index-purge.png)

### Agendador

Listar, alterar estado ou executar tarefas agendadas.

```shell
php joomla.php scheduler:list --help
php joomla.php scheduler:list
```

```shell
php joomla.php scheduler:state --help
php joomla.php scheduler:state (solicitação interativa para o id da tarefa)
```

```shell
php joomla.php scheduler:run --help
php joomla.php scheduler:run --id ID
php joomla.php scheduler:run --all
```

### Sessão

Realizar coleta de lixo de sessão.

```shell
php joomla.php session:gc --help
php joomla.php session:gc
php joomla.php session:gc --application administrator
```

```shell
php joomla.php session:metadata:gc --help
php joomla.php session:metadata:gc
```

### Site

Colocar o site offline ou online.

```shell
php joomla.php site:down --help
php joomla.php site:down
```

```shell
php joomla.php site:up --help
php joomla.php site:up
```

### Atualização

Verificar atualizações de extensões pendentes. Remove arquivos antigos que deveriam ter sido deletados durante uma atualização do Joomla.

```shell
php joomla.php update:extensions:check --help
php joomla.php update:extensions:check
```

```shell
php joomla.php update:joomla:remove-old-files --help
php joomla.php update:joomla:remove-old-files
```

![Saída da atualização do Joomla, removendo arquivos antigos](../../../en/images/command-line-interface/cli-update-remove-old-files.png)

### Usuário

Listar e gerenciar usuários.

```shell
php joomla.php user:list --help
php joomla.php user:list
```

```shell
php joomla.php user:add --help
php joomla.php user:add --username cinderella --name Cinderella --email cinders@localhost --usergroup Manager (solicitação para senha)
php joomla.php user:add (solicita dados)
```

![Saída da adição de usuário com solicitações](../../../en/images/command-line-interface/cli-add-user.png)

```shell
php joomla.php user:addtogroup --help
php joomla.php user:addtogroup (solicita dados)
php joomla.php user:addtogroup --usernam=cinderella --group=Manager
```

```shell
php joomla.php user:removefromgroup --help
php joomla.php user:removefromgroup (solicita dados)
php joomla.php user:removefromgroup --usernam=cinderella --group=Manager
```

```shell
php joomla.php user:reset-password --help
php joomla.php user:reset-password (solicita dados)
php joomla.php user:reset-password --username=cinderella (solicita senha)
```

```shell
php joomla.php user:delete --help
php joomla.php user:delete (solicita nome de usuário)
php joomla.php user:delete --username=cinderella (solicita confirmação - y para confirmar)
```

*Traduzido por openai.com*

