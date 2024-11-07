<!-- Filename: Visual_Studio_Code_Primer / Display title: Introdução ao Visual Studio Code -->

## VS Code - Um IDE Gratuito Popular

Da Wikipedia:

> Visual Studio Code, também conhecido como VS Code, é um editor de
> código-fonte criado pela Microsoft para Windows, Linux e macOS. As
> funcionalidades incluem suporte para depuração, realce de sintaxe,
> autocompletar código inteligente, snippets, refatoração de código e Git
> integrado. Os usuários podem alterar o tema, os atalhos do teclado, as
> preferências e instalar extensões que adicionam funcionalidades
> adicionais.

## Instalação

A página padrão do site do VS Code possui uma lista suspensa para cada plataforma suportada. As chances são de que sua plataforma já esteja pré-selecionada. Então, baixe e instale, e você está pronto para começar.

### Primeiros Passos

A página *Get Started* do VS Code possui alguns itens de *Início*, uma lista de itens *Recentes* e uma breve lista de *Tutoriais*. Se você é completamente novo no VS Code, recomendamos assistir a esses tutoriais. Eles levam apenas alguns minutos.

A Documentação do VS Code está disponível no menu *Ajuda / Documentação*. Os [Vídeos Introdutórios](https://code.visualstudio.com/docs/getstarted/introvideos) valem muito a pena assistir. Cada um leva de 2 a 6 minutos e oferece uma excelente introdução aos recursos do VS Code.

A documentação oficial é o lugar para onde ir se você quer procurar informações específicas.

### Extensões do VS Code

O VS Code pode ser usado para qualquer tipo de texto, incluindo uma ampla gama de linguagens de programação. Funciona com JavaScript sem adicionar extensões. Outras linguagens são detectadas por contexto, então, se você começar a criar e salvar código PHP, provavelmente será solicitado a instalar um pacote de suporte PHP.

Clique no ícone de *Extensões* na *Barra de Atividades* à esquerda para ver o que você tem instalado e o que é recomendado. Você precisará da extensão PHP Debug!

### Layout da Tela do VS Code

Alguns termos usados nas instruções subsequentes:

- **Barra de Atividades**: a barra estreita à esquerda da tela. Selecione qualquer ícone para abrir ou fechar a Barra Lateral Primária.
- **Barra Lateral Primária**: quando aberta, mostra detalhes da atividade selecionada.
- **Barra de Status**: na parte inferior da tela. Mostra o que está acontecendo.
- **Painel**: uma área abaixo dos editores de texto para exibir outras informações.

Selecione um ícone de layout no canto superior direito para abrir ou fechar qualquer um desses itens.

## Codificando uma Extensão Joomla

Para criar uma extensão, seu objetivo é criar um arquivo zip que você
possa instalar em um site Joomla funcionando. Portanto, você precisa de uma pasta para conter
seu código. Ela deve estar dentro do seu espaço de arquivos pessoais no seu laptop
ou computador desktop usado para desenvolvimento local. Não deve estar na árvore
do seu site. Por exemplo, você poderia usar *~/jextensions* para conter
subpastas para diferentes extensões. Eu uso *~/git* porque é curto
e fácil de soletrar, embora potencialmente confuso, pois cada subpasta
usa um repositório git separado.

### Código de Exemplo

Se você gostaria de algum código de exemplo para trabalhar, há uma extensão
disponível no GitHub chamada *mod_debugme*. Como o nome indica, é um
módulo com alguns bugs. Além do código do módulo, há um
arquivo *build.xml* para ilustrar uma maneira de automatizar a construção para testes
e criação de um arquivo zip.

O módulo é projetado para mostrar os próximos eventos (aniversários)
(3 por padrão) de uma lista armazenada em uma tabela de banco de dados. Você pode imaginar
isso sendo usado em um site de escritório ou família na expectativa de um bolo.

Pode ser melhor começar usando comandos git na linha de comando.
Primeiro, crie uma pasta para seu código e depois clone o repositório
remoto:
```sh
    mkdir ~/git
    cd ~/git
    git clone https://github.com/ceford/j4xdemos-mod-debugme
```
A resposta deve levar apenas alguns segundos:
```sh
    Cloning into 'j4xdemos-mod-debugme'...
    remote: Enumerating objects: 23, done.
    remote: Counting objects: 100% (23/23), done.
    remote: Compressing objects: 100% (16/16), done.
    remote: Total 23 (delta 3), reused 23 (delta 3), pack-reused 0
    Unpacking objects: 100% (23/23), done.
```
Você deve tirar um momento para olhar o conteúdo da pasta:
```sh
    cd j4xdemos-mod-debugme
    ls -al
    total 16
    drwxr-xr-x   6 ceford  staff   192  2 Sep 17:48 .
    drwxr-xr-x   3 ceford  staff    96  2 Sep 17:48 ..
    drwxr-xr-x  12 ceford  staff   384  2 Sep 17:48 .git
    -rw-r--r--   1 ceford  staff  1402  2 Sep 17:48 README.md
    -rw-r--r--   1 ceford  staff   927  2 Sep 17:48 build.xml
    drwxr-xr-x   8 ceford  staff   256  2 Sep 17:48 mod_debugme
```
A pasta *.git* contém informações sobre o repositório. O arquivo *README.md*
é um documento markdown que descreve este repositório. O arquivo *build.xml*
é um arquivo usado para construir a extensão usando uma ferramenta externa,
o Phing - descrito mais adiante. A pasta *mod_debugme* contém o código da
extensão.

### Instalar no Joomla

Comprimir a pasta da extensão para criar um arquivo zip instalável:
```sh
    zip -r mod_debugme.zip mod_debugme
```
Agora você pode instalar o arquivo zip no site Joomla que você usa para testar.
Após a instalação, você precisa criar um módulo de Site e atribuí-lo a uma
posição de módulo. Como é um módulo com erro, você poderia atribuí-lo a
uma posição em *Todas as páginas* enquanto trabalha nele; ou você poderia
atribuí-lo a uma posição em uma única página; ou você poderia posicioná-lo em um
artigo que tenha seu próprio item de menu.

Após a instalação, exclua o arquivo zip.

### Ativar o Modo de Depuração

Na Configuração Global do Joomla, defina *Sistema de Depuração* como *Sim* e
*Relatório de Erros* como *Máximo*.

Quando você abre uma página contendo o módulo com erro, você verá um rastreamento
de pilha indicando onde um erro foi acionado.

![rastreamento de pilha do vscode](../../../en/images/test-installations/vscode-primer-stack-trace.png)

Às vezes, o erro de codificação está na primeira linha do rastreamento de pilha.
Caso contrário, se o erro for acionado no código da biblioteca, por exemplo, ao
passar dados inválidos para uma função de banco de dados, o erro de codificação pode estar
mais abaixo na lista de chamadas de função.

## Abrir Pasta de Extensão no VS Code

No VS Code, use o item de menu Arquivo / Abrir Pasta para localizar e abrir a
pasta que contém sua cópia local do código da extensão *mod_debugme*.
Você deve ver algo semelhante ao seguinte:

![visualização de pasta no vscode](../../../en/images/test-installations/vscode-primer-screen.png)

Você pode ser capaz de diagnosticar o problema apenas lendo o código. No
caso do erro de *Classe "DebugHelper" não encontrada*, você verá que uma
declaração de *use* foi comentada algumas linhas antes. Esquecer de inserir uma
declaração de *use* é um erro comum durante o desenvolvimento inicial!

Corrija esse problema, depois compacte e instale o módulo novamente. Esse
passo pode se tornar um pouco tedioso quando você tem múltiplos problemas.
É aí que as ferramentas de construção são úteis.

## Phing

Phing é uma ferramenta de linha de comando, disponível para todas as plataformas, usada para construir pacotes de software usando instruções armazenadas em um arquivo XML, chamado build.xml por padrão. Para trabalhar com o código de extensão, ela pode ser usada para fazer duas coisas:

- copiar arquivos alterados da sua pasta de origem da extensão para os locais corretos na pasta do seu site.
- gerar um novo arquivo zip para novas instalações.

Baixe e instale o Phing. Outras ferramentas de build estão disponíveis! Você pode instalar o Phing na sua própria pasta bin ou em uma pasta bin do sistema. Você precisa anotar o caminho para o seu código Phing. Neste exemplo, é *~/bin/phing-latest.phar*. Você pode testá-lo na linha de comando após mudar para a pasta que contém seu código de extensão:
```sh
    cd ~/git/j4xdemos-mod-debugme
    php ~/bin/phing-latest.phar
```
Resposta:
```sh
    Buildfile: /Users/ceford/git/j4xdemos-mod-debugme/build.xml

    mod_debugme > main:
          ... Quaisquer arquivos copiados serão mencionados aqui
          [zip] Building zip: /Users/ceford/zips/mod_debugme.zip

    BUILD FINISHED

    Total time: 0.0863 seconds
```

## Tarefas do VS Code

Para executar o Phing de dentro do VS Code, você precisa criar um arquivo *tasks.json* na pasta *.vscode* na raiz da pasta *j4xdemos-mod-debugme*. Se esta última não existir, primeiro crie-a. Em seguida, crie o arquivo *tasks.json* e insira o seguinte código:
```json
{
    // Veja https://go.microsoft.com/fwlink/?LinkId=733558
    // para a documentação sobre o formato tasks.json
    "version": "2.0.0",
    "tasks": [
      {
        "label": "Build mod_debugme",
        "type": "shell",
        "command": "php ~/bin/phing-latest.phar",
        "windows": {
          "command": "php ~/bin/phing-latest.phar"
        },
        "group": "build",
        "presentation": {
          "reveal": "always",
          "panel": "shared"
        }
      }
    ]
}
```
Usuários do Windows precisam corrigir o comando específico do Windows. Agora, você pode compilar a extensão usando o menu *Terminal / Run Build Task*. O resultado do comando deve aparecer no Painel do Terminal abaixo da área de edição.
```sh
  *  Executando tarefa: php ~/bin/phing-latest.phar

  Buildfile: /Users/ceford/git/gitdemo/j4xdemos-mod-debugme/build.xml

  mod_debugme > main:

      [zip] Nada a fazer: /Users/ceford/zips/mod_debugme.zip está atualizado.

  BUILD FINISHED

  Total time: 0.1031 seconds

   *  O terminal será reutilizado pelas tarefas, pressione qualquer tecla para fechá-lo.
```
Podem ocorrer mensagens de erro incompreensíveis. A causa mais provável é ter caminhos inválidos para pastas no arquivo *build.xml* ou uma pasta não foi criada. Apenas mais um tipo de problema para depurar!

## Depuração

Você deve ser capaz de corrigir o primeiro bug apenas inspecionando o código. Problemas mais complicados exigem que você percorra o código com o depurador. Isso permite inspecionar variáveis para ver se elas contêm os valores que você espera, por exemplo, ao passar argumentos para funções de biblioteca.

### Configurações do *php.ini*

Para configurar a depuração com o Xdebug, você precisa fazer algumas entradas no início do seu arquivo *php.ini*.
```ini
    zend_extension="xdebug.so"
    xdebug.mode="debug"
    xdebug.client_port=9003
    xdebug.start_with_request = yes
```
Após salvar quaisquer alterações, reinicie o seu servidor Apache.

### Adicionar Janela do Site

Sua pasta de extensão contém apenas alguns arquivos, os ***sources*** dos arquivos instalados no seu site. A depuração em tempo de execução envolve definir pontos de interrupção nos arquivos do seu ***site***, então você precisa acessar esses arquivos. Você pode usar o menu *File / Add Folder to Workspace...* para adicionar a pasta do site ao seu Workspace. No entanto, há uma grande chance de acabar fazendo alterações nos arquivos do site em vez dos arquivos de origem. Portanto, provavelmente é melhor abrir uma janela separada do VS Code para depuração.

- **Abrir nova janela:** No menu do VS Code, selecione *File / New Window* e escolha a pasta que contém seu site Joomla.
- **Abrir pasta:** Na nova janela aberta, selecione *File / Open Folder...* no menu do VS Code. Encontre a pasta do seu site e selecione-a. Você deve ver uma lista de todos os arquivos do seu site Joomla na barra lateral primária.

### Configuração de Lançamento

Para que a depuração funcione no VS Code, você precisa de uma configuração de lançamento. Na raiz do seu site, crie uma pasta chamada *.vscode* (note o ponto inicial) contendo um arquivo chamado *launch.json* com o seguinte conteúdo:
```json
    {
        "configurations": [
            {
                "name": "Listen for XDebug",
                "type": "php",
                "request": "launch",
                "hostname": "0.0.0.0",
                "port": 9003,
                "stopOnEntry": true,
                "pathMappings": {
                    "/Users/ceford/Sites/j421rc2": "${workspaceFolder}"
                }
            }
        ]
    }
```
Lembre-se de substituir o item pathMappings neste exemplo pelos pathMappings reais do seu próprio site. O item stopOnEntry irá pausar a execução na primeira linha do código PHP executado.

### Depurar *mod_debugme*

Agora você está pronto para encontrar e corrigir bugs no módulo instalado.

- **Encontrar código do módulo:** Encontre o primeiro bug na linha 16 de JROOT/modules/mod_debugme/mod_debugme.php.
- **Definir ponto de interrupção:** Clique no espaço à esquerda do número 16. Um pequeno círculo vermelho pálido aparecerá enquanto você passa o cursor e se tornará totalmente vermelho após clicar, indicando que um ponto de interrupção foi definido.
- **Iniciar depuração:** No menu do VS Code, selecione *Run / Start Debugging*. No seu navegador, recarregue seu site. A janela do VS Code deve reaparecer com o código parado na primeira linha do arquivo *index.php* do site. No topo da tela há alguns ícones para controlar o processo de depuração. Eles devem ser autoexplicativos. Se não, veja-os na Ajuda / Documentação do VS Code.
- **Continuar:** Selecione o botão continuar - o código seguirá até o seu primeiro ponto de interrupção. Examine o código para ver qual é o problema.
- **Hover:** Se você passar o mouse sobre uma variável que recebeu um valor, aparecerá uma pequena dica de ferramenta resumindo os atributos dessa variável. Não há dica de ferramenta para variáveis que não receberam valores.
- **Variáveis:** A coluna da esquerda contém mais informações sobre o estado do código no ponto de interrupção. São muitas para cobrir aqui. Explore conforme necessário!
- **Parar Depuração:** Provavelmente é melhor selecionar o ícone Continuar, caso contrário, a página da web é entregue em branco. Caso contrário, você poderia usar o botão Stop ou o menu Run / Stop Debugging.

### Corrigir um Bug

**Lembre-se:** Não corrija o bug no código do site! Corrija-o no código-fonte!

Corrija o código-fonte e depois use *Terminal / Run Build Task...*.

Reinicie a depuração.

### Dicas

Alguns problemas não tão óbvios:

- Você corrige o primeiro bug, mas ele ainda trava nessa linha. Olhe em mod_debugme.xml para ver onde o src das classes com namespace está definido. Quando corrigido no código-fonte, você precisará reinstalar o arquivo zip ou excluir *administrator/cache/autoload_psr4.php*. Quando ausente, o Joomla reconstrói esse arquivo a partir dos arquivos de manifesto. Mas se ele tiver uma entrada incorreta ou ausente, ela não é corrigida até que a extensão seja reinstalada.
- Às vezes, você precisa definir um ponto de interrupção algumas linhas antes da linha em que o erro ocorre, especialmente se desejar verificar os valores passados para chamadas de função.
- A tabela *xxx.yyy\\debugme* não existe. Ah sim, o código para criar uma tabela na instalação e remover na desinstalação nunca foi criado. Você precisará executar uma consulta SQL no phpMyAdmin usando o conteúdo do arquivo *mod\\debugme.sql*. Lembre-se de alterar *\#\\* nos nomes das tabelas para o prefixo do seu banco de dados. E quando ainda falhar, verifique o nome da tabela no código.

## Captura de Tela

Quando tudo estiver corrigido, isso é o que você poderá ver:

![visualização do módulo depurado no vscode](../../../en/images/test-installations/vscode-primer-debugme-fixed.png)

Dias de comemoração?

## Referências

Da Documentação do Joomla!: [Visual Studio Code](https://docs.joomla.org/Visual_Studio_Code) também aborda a configuração de outras ferramentas, como CodeSniffer e PHPUnit.

*Traduzido por openai.com*

