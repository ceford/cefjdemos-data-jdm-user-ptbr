<!-- Filename: Setting_up_Apache,_PHP_and_MySQL_manually / Display title: Configurando Apache, PHP e MySQL manualmente  -->

## Visão Geral

Aqui está uma visão geral dos passos para configurar o Apache, PHP e MySQL em um ambiente Windows, além de referências a várias ferramentas relacionadas para manter e trabalhar com a maioria das tarefas relacionadas ao Joomla!.

Para que as instruções sejam claras e sucintas, assumiremos que, sempre que não estivermos dando uma instrução explícita, você permitirá que os caminhos de configuração padrão sejam aplicados sem modificação.

### Aviso

Se você já tem algum dos pacotes AMP pré-instalados em sua máquina:

- Voltar para o seu pacote AMP será difícil. As várias instalações que faremos abaixo sobrescreverão valores de registro e farão alterações gerais no ambiente. (Isso se aplica pelo menos ao ambiente PC/Windows.)
- Se você precisar manter qualquer configuração (Apache, MySQL ou PHP) ou dados (seus sites existentes e bancos de dados relacionados), antes de tentar seguir estas instruções, faça backups adequados.

(precisa ser expandido com conselhos específicos sobre como alcançar o acima...)

## Configuração do MySQL

1. Baixe o <a href="https://dev.mysql.com/downloads/mysql/" rel="nofollow noreferrer noopener">instalador MySQL</a> apropriado para sua plataforma.
2. Inicie a instalação e escolha o caminho de instalação Personalizado.
3. Clique em cada etapa do processo de instalação até finalizar.
4. Agora você será apresentado ao *Assistente de Configuração da Instância do Servidor MySQL*.
   1. Certifique-se de que a *Configuração Padrão* esteja selecionada e clique em Avançar.
   2. Se você já tiver o MySQL instalado, pode receber a mensagem *Um serviço Windows com o nome MySQL já existe. Por favor, desinstale este serviço corretamente ou escolha um nome diferente para o novo serviço.* Nesse caso, escolha um nome alternativo para o serviço.
   3. Na próxima janela, marque *Incluir Diretório Binário no Caminho Windows (PATH)*. Ao fazer isso, você poderá acessar as várias utilidades MySQL pela linha de comando.
   4. Na próxima janela, você poderá criar uma senha para o seu usuário root do MySQL, o usuário com o mais alto nível de acesso no seu servidor.
   5. Na janela final, todas as mudanças que você configurou até agora serão salvas quando você pressionar o botão *Executar* e o serviço do Windows para esta instância será iniciado.

### Notas

1. Para tornar as instruções o mais acessíveis possível, pulamos vários cenários de configuração da sua instância MySQL, como a capacidade de realocar seus arquivos de banco de dados.
2. O MySQL é instalado por padrão com um modo ESTRITO, que pode causar alguns erros ao usar extensões ou aplicações que não tenham considerado isso.

### Recursos do MySQL

- <a href="https://www.heidisql.com/" class="external text" rel="nofollow noreferrer noopener">HeidiSQL</a> Substituição completa do cliente phpMyAdmin, fácil de usar e extensível, em constante desenvolvimento.
- <a href="https://dev.mysql.com/downloads/workbench/" class="external text" rel="nofollow noreferrer noopener">MySQL Workbench</a> Várias ferramentas entre as quais você apreciará o Administrador, que ajuda a configurar sua instância MySQL. Requer o <a href="https://dotnet.microsoft.com/en-us/" class="external text" rel="nofollow noreferrer noopener">.Net framework</a>.
- <a href="https://www.phpmyadmin.net/" class="external text" rel="nofollow noreferrer noopener">phpMyAdmin</a> Um poderoso cliente MySQL baseado na web para administrar qualquer aspecto relacionado ao MySQL.
- <a href="https://dev.mysql.com/doc/" class="external text" rel="nofollow noreferrer noopener">Documentação do MySQL</a>

## Configuração do Apache

1.  <a href="https://httpd.apache.org/download.cgi" class="external text"
     rel="nofollow noreferrer noopener">Baixe o
    instalador</a> de sua preferência.
2.  Execute o assistente de instalação e clique em cada etapa até chegar
    à janela de Informações do Servidor. Preencha as opções abaixo, respectivamente,
    e na ordem dada, em cada um dos campos, a menos que você tenha
    requisitos específicos sobre como seu servidor web deve ser configurado:
    1.  localhost,
    2.  localhost e
    3.  admin@localhost.
3.  Prossiga pelo assistente, que instalará e iniciará o servidor web Apache
    como um serviço do Windows.
4.  Na barra de status do Windows, você verá uma pena rosa com um botão de play verde
    indicando que o Apache está ativo e funcionando. Aponte seu navegador para
    <a href="http://localhost/"
    rel="nofollow noreferrer noopener">http://localhost/</a> e você
    deve ver uma página indicando que está funcionando.
5.  Vamos agora para o local onde o Apache está instalado, que
    geralmente é em *C:\Program Files\Apache Software
    Foundation\Apache2.2*, e explore os vários diretórios:
    1.  *bin* - contém os vários arquivos binários, alguns dos quais são
        listados abaixo. Para acessar esses aplicativos, a maioria
        baseada em comando, precisamos adicionar o caminho para o
        diretório *bin* em nossa variável PATH global. Para fazer isso, clique com o
        botão direito em Meu Computador \> Propriedades \> Avançado \> Variáveis
        de Ambiente e, na lista de Variáveis do Sistema, localize e selecione
        a Variável PATH e clique em Editar. Adicione um ponto e vírgula ao final,
        se já não estiver lá, seguido pelo caminho absoluto para o seu diretório bin.
        Clique para fechar o diálogo Propriedades do Sistema aceitando.
        1.  *httpd.exe* é o próprio servidor web Apache, que é
            gerado para vários processos filhos enquanto atende a tantos
            pedidos de clientes simultâneos quanto requeridos pela
            diretiva MaxClients;
        2.  *ab.exe* é uma ferramenta de benchmarking que vem com o Apache
            permitindo ver quão bem sua aplicação pode performar
            por unidade de tempo.
    2.  *conf* - pasta onde vários arquivos de configuração estão localizados,
        dos quais os seguintes são de maior interesse em nosso caso:
        1.  *httpd.conf* - a maioria das diretivas do servidor está localizada
            neste arquivo e, para fácil acesso, você deve associar o
            tipo de arquivo *.conf* com um editor amigável, ou seja, qualquer coisa
            que não seja o Bloco de Notas padrão.
        2.  *extra\httpd-vhosts.conf* - contém diretivas que permitem
            usar seu servidor local como host virtual, ou seja,
            capaz de rodar vários servidores em seu PC. Um cenário de uso é
            durante uma fase de desenvolvimento, se você deseja mapear o
            domínio real para o qual está trabalhando para sua cópia local,
            você poderá fazer isso fazendo pequenos ajustes neste arquivo.
            Vamos discutir isso com mais detalhes abaixo.
    3.  *htdocs* - a raiz padrão do servidor web, este é o local onde o
        <a href="http://localhost/"
        rel="nofollow noreferrer noopener">http://localhost/</a> é
        mapeado, ou seja, se você não reconfigurá-lo no *httpd.conf* acima.
    4.  *logs* - logs de acesso e erro, usados ao tentar resolver vários
        problemas relacionados ao seu servidor ou até mesmo à sua aplicação.

### Recursos do Apache

- A
  <a href="https://httpd.apache.org/docs/current/" class="external text"
   rel="nofollow noreferrer noopener">documentação de referência do Apache</a>

## Configuração do PHP

1.  <a href="https://windows.php.net/download/" class="external text"
     rel="nofollow noreferrer noopener">Baixe o PHP</a>
    e escolha geralmente o VC6 x86 Thread Safe no formato Zip. As várias
    opções estão relacionadas a como a base de código do PHP foi compilada para binário e provavelmente não precisam ser uma preocupação agora.
2.  Crie uma pasta em C:\Program Files\\ (ou onde quer que seu diretório de programas esteja localizado) chamada PHP.
3.  Localize o arquivo Zip baixado, mova-o para a pasta recém-criada e descompacte-o diretamente na pasta.
4.  Vamos agora adicionar o caminho do PHP à nossa variável PATH global seguindo as instruções acima.

### Configurando o PHP

A configuração envolve a edição do arquivo *php.ini*. Um arquivo de exemplo para diferentes cenários já está na sua pasta PHP. Vamos renomear *php.ini-development* para *php.ini* e abri-lo no seu editor de texto favorito. Os valores comuns para ajustar são os seguintes, e todas essas variáveis estão bem documentadas no arquivo *php.ini*. (Note que esta configuração se aplica a todos os seus projetos no servidor):

- *max_execution_time* - sempre que você tiver scripts que demoram muito para serem executados e o servidor retornar vários resultados inesperados, o que você acha que se deve ao fato de não conseguir executar o processo inteiro.
- *memory_limit*
- *error_reporting*
- *display_errors*
- *log_errors* - uma variável da qual você precisará ter atenção em cenários de produção.
- *upload_tmp_dir*
- *upload_max_filesize*
- *extension_dir* - para evitar complicações, vamos indicar o diretório onde as seguintes extensões estão localizadas, descomentando esta variável e atribuindo a localização absoluta da pasta. A linha completa deve ser assim:
    extension_dir = "C:\Program Files\PHP\ext"

- A seção de extensões dinâmicas contém vários módulos adicionais que você deseja carregar, e os comentados são os que vêm pré-embalados com o PHP e podem ser encontrados no diretório *ext* na sua pasta PHP. Se você quiser ativar alguma, basta remover o comentário, como deve fazer com as seguintes extensões:
  - php_curl.dll
  - php_gd2.dll
  - php_mbstring.dll
  - php_mysql.dll
  - php_mysqli.dll
  - php_pdo.dll
  - php_pdo_mysql.dll
  - php_xsl.dll
- session.save_path

### Configurando o Apache para Trabalhar com o PHP

Agora que configuramos o PHP para funcionar como queremos, vamos fazer o mesmo no Apache.

- Abra *httpd.conf* e, na seção "Dynamic Shared Object (DSO) Support", adicione as seguintes diretivas. (Se você localizou sua pasta PHP de maneira diferente, faça a alteração correspondente para php5apache2_2.dll abaixo.):
    LoadModule php5_module "C:/Program Files/PHP/php5apache2_2.dll"
    AddType application/x-httpd-php .php

- No DirectoryIndex, adicione *index.php* e *index.htm* como possíveis arquivos a serem servidos quando o diretório for solicitado, como segue:
    DirectoryIndex index.html index.htm index.php

- No final do arquivo, adicione a seguinte linha que indicará onde o arquivo *php.ini* está localizado:
    PHPIniDir "C:/Program Files/PHP"

### Reinicie e Teste o PHP

Assim que você fizer qualquer alteração no *php.ini*, *httpd.conf* ou em qualquer outro arquivo de configuração, você precisará reiniciar o Apache para ver o efeito das mudanças. Então, vamos agora reiniciar o Apache usando a ferramenta Apache Monitor que você pode encontrar na barra de status do Windows. Esperamos que você não seja solicitado com nenhuma caixa de diálogo e que a Apache Monitor continue a rodar em verde.

Agora vamos testar se o PHP está funcionando. Vá para o diretório raiz do documento do seu servidor web (no caso padrão *C:\Program Files\Apache Software Foundation\Apache2.2\htdocs*) e adicione um arquivo chamado *phpinfo.php* com o seguinte conteúdo:


Isso renderizará uma página contendo informações sobre sua configuração do PHP e sobre os vários módulos/extensões que estão atualmente carregados. Aponte seu navegador para
<a href="http://localhost/phpinfo.php"

rel="nofollow noreferrer noopener">http://localhost/phpinfo.php</a>.

### Instalando e Configurando o *xdebug*

1.  Aponte seu navegador para
    <a href="https://xdebug.org/wizard" class="external text"
     rel="nofollow noreferrer noopener">Assistente de Instalação do
    Xdebug</a>. Esta página ajudará você a encontrar uma versão adequada do Xdebug.
2.  Copie a página inteira da página *phpinfo* que executamos acima e cole-a na área de texto e siga as instruções fornecidas para instalação.

### Recursos do XDebug

- O <a href="https://www.php.net/docs.php" class="external text"
   rel="nofollow noreferrer noopener">Manual do PHP</a>
  Excelente documentação atualizada com comentários adicionais valiosos dos usuários. Versões para download estão disponíveis.
- A
  <a href="https://xdebug.org/docs/" class="external text"
  rel="nofollow noreferrer noopener">Documentação do Xdebug 3</a>

*Traduzido por openai.com*

