<!-- Filename: How_do_UNIX_file_permissions_work%3F / Display title: Permissões de Arquivos UNIX -->

As permissões de arquivos Unix/Linux podem ser confusas. As permissões básicas do UNIX vêm em três tipos:

    Permissões do Proprietário: Controlam seu próprio acesso aos arquivos.
    Permissões do Grupo: Controlam o acesso para você e qualquer pessoa no seu grupo.
    Permissões de Outros: Controlam o acesso para todos os demais.

No Unix, ao configurar permissões, o servidor permite que você defina diferentes permissões para cada uma dessas três categorias de usuários. Em um ambiente de servidor Web, as permissões são usadas para controlar quais proprietários de sites podem acessar quais diretórios e arquivos.  

## Como são as permissões do Unix?

Ao visualizar seus arquivos via linha de comando usando o comando Unix `ls -l`, você verá linhas como as seguintes, uma para cada arquivo e diretório:

```
drwxr-xr-x@  7 username  usergroup    224 13 Feb 10:48 includes
-rw-r--r--@  1 username  usergroup   1060 13 Apr 21:00 index.php
```

Explicação:
* O primeiro caractere na linha é d para diretório ou - para arquivo, ou ...
* Os próximos 9 caracteres são 3 grupos de 3 representando leitura (r), escrita (w) e execução (x) ou um símbolo de menos (-) indicando sem acesso para cada um dos Dono, Grupo e Outros.
* O símbolo @ é um dos vários atributos estendidos possíveis,
* O número antes do nome do usuário é a profundidade do diretório.
* Os dois nomes são o nome de usuário do proprietário e o grupo de usuários,
* O inteiro seguinte é o tamanho do arquivo em bytes.
* A data seguinte tem hora para itens recentes ou ano para itens mais antigos.
* Por último, está o nome do arquivo ou diretório.

Em uma ferramenta de FTP, a ordem pode ser diferente e pode haver mais ou menos informações.

### Dono (Usuário) refere-se ao nome de usuário

O Dono (Usuário) normalmente é você, essas permissões serão aplicadas ao nome da sua conta de hospedagem.

### Grupo refere-se ao grupo de usuários

As permissões de Grupo serão aplicadas a outras pessoas que estão no mesmo grupo que você. Em um ambiente de hospedagem, muito raramente há outras pessoas no mesmo grupo que você. Isso protege seus arquivos e diretórios de serem disponibilizados para qualquer outra pessoa que também possa ter uma conta de hospedagem no mesmo servidor que você.

### Outros refere-se a todos os outros

As permissões de Outros serão aplicadas a qualquer outra pessoa no servidor que não seja você ou não esteja no seu grupo. Portanto, em um ambiente de Servidor Web, considerando que normalmente ninguém mais está no seu grupo, isso significa todos os outros que acessam o servidor, exceto você. Cada um dos três conjuntos de permissões é definido da seguinte maneira:

    r = Permissões de leitura
    w = Permissões de escrita
    x = Permissões de execução

    Dono Grupo Outros
    r w x r w x r w x

Como muitos de vocês já sabem, as permissões normalmente são expressas como um valor numérico, algo como 755 ou 644. Então, como isso se relaciona com o que discutimos acima? Cada caractere das permissões é atribuído a um valor numérico, este é atribuído em cada conjunto de três, portanto, precisamos usar apenas três valores e reutilizá-los para cada conjunto.

    Dono Grupo Outros
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Agora que temos um valor que representa cada permissão, podemos expressá-los em termos numéricos. Os valores são simplesmente somados nos respectivos conjuntos de 3, o que nos dará apenas três números que nos dirão quais permissões estão sendo configuradas. Se nos for dito que um arquivo tem as permissões de 777, isso significaria que o seguinte é verdade.

    Dono Grupo Outros
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Assim...

      4+2+1 4+2+1 4+2+1
    =   7     7     7

O Dono do arquivo teria permissões completas de Leitura, Escrita e Execução, o grupo também teria permissões completas de Leitura, Escrita e Execução, e o resto do mundo também poderia Ler, Escrever e Executar o arquivo. As permissões padrão, atribuídas automaticamente a arquivos e diretórios pelo servidor, normalmente são:

    Arquivos = 644
    Diretórios = 755

Essas permissões permitiriam, para arquivos;

    644 = rw- r-- r--
    O Dono tem Leitura e Escrita
    O Grupo tem apenas Leitura
    Outros têm apenas Leitura

e para diretórios;

    755 = rwx r-x r-x
    O Dono tem Leitura, Escrita e Execução
    O Grupo tem apenas Leitura e Execução
    Outros têm apenas Leitura e Execução

Agora, as coisas podem ficar um pouco complicadas quando começamos a falar sobre Servidores Web compartilhados, o software do Servidor Web estará sendo executado com seu próprio nome de usuário e nome de grupo, a maioria dos servidores está configurada para usar "apache" e "apache" ou "nobody" e "nobody" como nome de usuário e nome de grupo. Aqui está o problema: seu Servidor Web opera como seu próprio usuário, e este usuário não é você nem está no seu grupo, então os primeiros dois conjuntos de permissões não se aplicam a ele. Apenas as permissões do mundo (outros) se aplicam. Portanto, se você configurar um conjunto de permissões semelhante a 640 nos arquivos do seu site, seu Servidor Web não poderá executar os arquivos do seu site.

    640 = rw- r-- ---
    O Dono tem Leitura e Escrita
    O Grupo tem apenas Leitura
    Outros não têm direitos

O Servidor Web não tem quaisquer permissões e não pode Executar, Escrever ou, mais importante, nem mesmo Ler o arquivo para entregar seu conteúdo ao navegador de um visitante do site. Se um diretório receber 750 permissões, isso teria o mesmo efeito, porque o Servidor Web não tem sequer permissões para ler arquivos no diretório, mesmo que os arquivos dentro desse diretório tenham permissões favoráveis.

    750 = rw- r-x ---
    O Dono tem Leitura e Escrita
    O Grupo tem Leitura e Execução
    Outros não têm direitos

Os diretórios têm uma peculiaridade extra, se um diretório não tiver a permissão de Execução configurada no conjunto do Mundo, mesmo que Leitura e Escrita estejam configurados, se o programa não for executado como o usuário ou grupo, ainda não poderá acessar os arquivos dentro do diretório. A configuração de Execução permite que o programa "Execute" comandos no diretório, portanto, sem ele, o programa (no nosso caso, um Servidor Web) não pode executar o comando "Ler", assim não pode entregar seu arquivo ao navegador dos usuários.

## Como isso se Relaciona ao Joomla?

Boa pergunta, bom, em primeiro lugar, isso seria importante durante o processo de Instalação pela Web. Se você se lembra de quando executou a Instalação pela Web do Joomla!, estávamos procurando por diretórios específicos que precisavam ser designados como graváveis. Vemos um número considerável de postagens afirmando que houve problemas durante a instalação com permissões ou perguntando quais permissões são recomendadas. Alguns até consideram a mensagem solicitando permissões "graváveis" muito vaga.

Infelizmente, como o Instalador Web não sabe como o seu servidor está configurado, ele não pode ser mais específico; no entanto, uma vez que você entender as configurações de permissões e souber um pouco sobre ambientes de Servidor Web, você verá que o termo *gravável* é, na verdade, muito específico e uma descrição mais que adequada do que o Joomla! necessita. Pensando na informação acima, você pode lembrar que há três lugares onde permissões de *gravação* podem ser definidas:

    Proprietário Gravável
    Grupo Gravável
    Outros Gravável

Lembrando também que o Servidor Web geralmente não roda como o seu usuário ou no mesmo grupo. Quando você executa o Instalador Web a partir de um navegador, é o Servidor Web que tenta acessar os arquivos, assim, são as permissões "Outros" que se aplicam a ele. Se as permissões "Outros" não permitirem que o Servidor Web Leia, Grave ou Execute comandos nos diretórios do Joomla!, você receberá uma mensagem dizendo que os diretórios não são *graváveis*.

Nesse caso, você precisará configurar as permissões "Outros" para serem "7" nos diretórios listados no Instalador Web. Assim, suas permissões totais podem ser algo como 757, no pior caso você pode precisar definir 777. Essas permissões muito abertas podem ser redefinidas para 755 após a execução do instalador para ajudar na segurança dos seus diretórios e arquivos.

    757 = rwx r-x rwx
    Proprietário tem Leitura, Gravação e Execução
    Grupo tem Leitura e Execução
    Outros têm Leitura, Gravação e Execução

Só para tornar as coisas ainda mais confusas, muitas empresas de hospedagem usam um software chamado phpsuExec ou suExec, essas ferramentas mudam a forma como o Servidor Web funciona, onde o Servidor Web normalmente não rodaria como seu nome de usuário, neste caso, ele roda. O uso das permissões *outros* pode não ser necessário, agora você pode apenas precisar configurar diretórios para serem *graváveis* pelo seu próprio nome de usuário e nome de grupo, isso permite que as permissões do diretório sejam definidas como 755 ou 775 em vez de 757 ou 777.

    755 = rwx r-x r-x
    Proprietário tem Leitura, Gravação e Execução
    Grupo tem Leitura e Execução
    Outros têm Leitura e Execução

    775 = rwx rwx r-x
    Proprietário tem Leitura, Gravação e Execução
    Grupo tem Leitura, Gravação e Execução
    Outros têm Leitura e Execução

O Servidor Web ainda precisará ter Execute definido para o nome de usuário e permissões de Leitura, Execute para o nome do grupo para que possa executar o comando de Leitura nos arquivos dentro do diretório. Novamente, essas permissões podem ser rebaixadas para 755 após o Instalador Web ser concluído. Essa é a base para os diretórios, e quanto aos arquivos? Aqui é onde as coisas ficam um pouco mais simples. A maioria dos arquivos que o Joomla! utiliza ficará bastante contente com as permissões padrão 644.

    644 = rw- r-- r--
    Proprietário tem Leitura, Gravação
    Grupo tem Leitura
    Outros têm Leitura

Isso é válido se você não precisar gravar nos arquivos a partir do Servidor Web, as mesmas regras se aplicam a diretórios se você tiver essa necessidade. Um arquivo que você pode querer que seja "Gravável" pelo Servidor Web é o seu arquivo configuration.php. Este é o arquivo de configuração do Joomla!, se você planeja alterar a configuração por meio da interface de Administração Web, então este arquivo precisará ser Gravável pelo Servidor Web.

Se o seu servidor precisasse que as permissões de diretório fossem definidas como "Outros" Gravável para a instalação, então este arquivo provavelmente também precisará ser 757 ou 777. No entanto, deixar este arquivo como 757 ou 777 é perigoso, pois você está permitindo que todos tenham acesso de "Gravação", muitos exploits de sites usam isso a seu favor, por isso, em geral, não é recomendado deixar este arquivo com essas permissões.

Se o seu Servidor Web tem uma das ferramentas SU instaladas e você apenas precisou configurar 755 nos diretórios para a instalação, então provavelmente também precisará apenas definir 755 ou 775 neste arquivo para permitir edição através da interface de Administração, e essas permissões geralmente são aceitas como mais seguras do que 757 ou 777.

Em conclusão, que permissões devem ser configuradas para a instalação do Joomla!? Bem, como você pode ver, depende!

Eu sei que isso não é tão útil quanto você gostaria e certamente não é uma resposta definitiva, mas em geral, após a instalação, qualquer configuração insegura de "7" pode ser redefinida para algo mais seguro. Por exemplo:

    Arquivos = 644
    Diretórios = 755

Essas permissões permitiriam, para arquivos;

    644 = rw- r-- r--
    Proprietário tem Leitura e Gravação
    Grupo tem apenas Leitura
    Outros têm apenas Leitura

e para diretórios,

    755 = rwx r-x r-x
    Proprietário tem Leitura, Gravação e Execução
    Grupo tem apenas Leitura e Execução
    Outros têm apenas Leitura e Execução

Se você tiver acesso ao shell SSH, os seguintes comandos podem ser executados a partir da linha de comando para redefinir todos os arquivos e diretórios de volta para os padrões do servidor de 755 e 644. Troque para o diretório principal ("/") da sua instalação do Joomla!, então execute:

    find . -type f -exec chmod 644 {} \;
    find . -type d -exec chmod 755 {} \;

Se você tiver apenas acesso FTP, isso pode ser uma tarefa muito demorada; no entanto, a menos que você tenha alterado mais diretórios durante a instalação do que foi solicitado, você só precisará redefinir cerca de 10 diretórios e o arquivo *configuration.php*.

Lembre-se de que para instalar qualquer extensão ou template após a instalação do Joomla! real, você pode precisar elevar novamente as permissões padrão nos diretórios apropriados apenas para o período de instalação; você pode então rebaixá-las novamente após a instalação do add-on.

Se você decidir usar *caching*, o diretório de cache precisará ser *gravável* pelo usuário do Servidor Web para permitir que ele escreva seus arquivos temporários.

## Corrigir permissões recursivamente

Em uma janela de terminal, começando a partir do diretório raiz do site Joomla, use os seguintes comandos para definir as permissões de arquivos e pastas para os padrões do Joomla.

```bash
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
```

Nota: O comando find assume que deve começar a partir do diretório atual. Para garantir, vá para o seu diretório public_html e especifique um caminho como o primeiro argumento. Alguns shells, como bash no Apple OS X, precisam ter um caminho especificado no comando find.

Teste todas as extensões de terceiros após alterar as permissões.

*Traduzido por openai.com*  

