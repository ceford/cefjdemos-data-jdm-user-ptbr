<!-- Filename: jdocmanual?manual=user&heading=system&filename=backup.md / Display title: Backup  -->

## Acidentes Acontecem!

Muito tempo, esforço e dinheiro são investidos na criação e manutenção de um site. É uma pena perder tudo isso em um acidente inesperado. Fazer backup é fácil para sites comuns. Sites grandes ou especializados provavelmente precisam de aconselhamento especializado.

## Estrutura de Backup

Os sites Joomla! consistem de duas partes:

* Os **arquivos** localizados no diretório raiz do Joomla. Entre as atualizações, os arquivos podem não mudar muito, pois são principalmente relacionados ao código. Novas imagens e documentos podem ser adicionados e, talvez, substituições de templates.
* O **banco de dados** localizado em outro lugar no servidor host. O banco de dados contém a maioria do conteúdo do site e pode mudar bastante à medida que os usuários adicionam ou editam conteúdo.

Todo proprietário de site precisa de uma estratégia para recuperação do site em caso de desastre. O conselho comum nos Fóruns é **restaurar o último backup**. Então, decida o que fazer backup e com que frequência.

Os serviços de hospedagem frequentemente tiram **instantâneos** dos sites dos clientes e podem restaurar um site para a condição de ontem, na semana passada ou no mês passado. Mas isso pode cobrir tudo na conta, como emails e outros pacotes de software. Não confie nisso para a recuperação do site Joomla.

Este artigo descreve alguns métodos comuns **gratuitos** para fazer backup de sites Joomla. Você pode optar por pagar por ferramentas e/ou serviços de backup, mas isso não está coberto aqui.

## Akeeba Backup

Se você usar o menu do Administrador para navegar até **Sistema / Instalar Extensões / Instalar da Web**, o primeiro item na lista é *Akeeba Backup*. Ele está em primeiro na lista porque possui o maior número de avaliações positivas. Não é preciso dizer que ele tem uma longa história e uma reputação impecável. Há uma versão gratuita e uma versão paga com alguns recursos extras. Esse é um modelo de negócios comum para desenvolvedores de Extensões. Não fique receoso! A versão gratuita é fácil de usar, não tem distrações e é suficiente para a maioria dos sites. O que ela faz:

* O Akeeba Backup analisa sua instalação para determinar as configurações ideais para criar um arquivo de backup.
* Ele cria um arquivo de backup composto contendo todos os arquivos do site e o conteúdo do banco de dados.
* Armazena backups com registro de data e hora para gerenciar, baixar ou excluir conforme necessário.
* O download é feito em um arquivo .jpa. Recomenda-se o uso de FTP para fazer o download.
* Há um aplicativo separado chamado Akeeba Kickstart para descompactar o arquivo .jpa. Tudo isso é descrito na página Gerenciar Backups do Akeeba.
* Após a descompactação, o site é instalado com um instalador Akeeba em uma sequência similar à instalação do Joomla.
* O instalador altera a configuração para a restauração em um local diferente e solicita os detalhes do novo banco de dados.

O único problema que pode ocorrer é que o arquivo de backup pode ser muito grande e você pode exceder sua cota de espaço em disco se permitir que os backups se acumulem.

Experimente! Não custa nada e leva minutos, em vez de horas.

## Ferramentas do Host

A maioria dos serviços de hospedagem oferece ferramentas de backup. Exemplo:

### cPanel

Na página **Ferramentas**, o item *Arquivos* possui um link de *Backup*. A página **Backup** tem três opções:

* **Backup Completo:** Um backup completo cria um arquivo de todos os arquivos e configurações do seu site. Você pode usar este arquivo para mover sua conta para outro servidor ou para manter uma cópia local de seus arquivos.
* **Backup Parcial**
    - Baixar um Backup do Diretório Inicial
    - Baixar um Backup do Banco de Dados (com uma lista de bancos de dados)

Também há opções para **Restaurar** cada um desses tipos de backup. Opções para produzir backups automáticos podem estar disponíveis também.

Pastas individuais podem ser comprimidas em vários formatos adequados para download usando o Gerenciador de Arquivos do cPanel. Um banco de dados pode ser exportado usando o phpMyAdmin. Nenhum desses métodos é coberto aqui.

## Ferramentas Locais

Há ocasiões em que você pode precisar fazer um backup de um site localmente em um laptop ou em um computador de mesa do escritório. Por exemplo, você pode querer copiar um site para/de um serviço de hospedagem para/do seu computador local. Se você tiver uma instalação local do Joomla, pode usar o Akeeba Backup conforme descrito acima. Caso contrário, você pode fazer backup do banco de dados e dos arquivos do Joomla separadamente.

### mysqldump

Se você estiver usando MySQL, provavelmente terá disponível a ferramenta de linha de comando *mysqldump*. Tente este comando:

```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname > ~/tmp/dbname-dump.sql
```
onde `root` é um usuário que tem acesso ao banco de dados e `dbname` é o nome do banco de dados que você deseja exportar. Pode ser solicitado que você insira a senha.

Você também pode canalizar a saída para um comando zip ou gzip:
```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname | gzip > ~/tmp/dbname-dump.sql.gz
```

### phpMySQL

Para realizar a mesma tarefa com sua instalação local do phpMyAdmin, abra-o e selecione o banco de dados que deseja exportar. Selecione o botão **Exportar** no topo da tela. Por padrão, a exportação *Rápida* usa SQL como formato de saída. Selecione o botão **Exportar** para tentar isso. Você será solicitado a indicar um arquivo de saída.

Se você selecionar a opção *Personalizado*, poderá escolher uma opção de Compressão de Saída, seja nenhuma, zipada ou gzipada. Tente uma exportação comprimida e selecione o botão **Exportar**.

Você precisa **verificar** o banco de dados exportado. Crie um novo banco de dados, talvez `animporttest`, para que ele fique no topo da sua lista de bancos de dados. Com o novo banco de dados vazio selecionado, use o botão **Importar** na parte superior da tela. No formulário de importação, clique em **Procurar** para encontrar o arquivo que você exportou e, em seguida, selecione o botão **Importar**.

Valeu a pena a **verificação**. A exportação gzip só exportou três tabelas. A exportação zip funcionou bem. Isso foi evidente nos tamanhos dos arquivos exportados. O arquivo zip tinha 4Mb, mas o gzip tinha apenas 75Kb. Deve haver um bug em algum lugar!

### Zip e Gzip

Essas ferramentas de linha de comando são bastante onipresentes e são frequentemente usadas em interfaces gráficas. Por exemplo, no Finder do Mac, posso selecionar um diretório contendo um site do Joomla, clicar com o botão direito e selecionar **Comprimir**. Leva alguns segundos para fazer um arquivo zip e não afeta o original.

## Restaurando um Backup

Conselhos comuns dos Fóruns Joomla:

* Não restaure um backup em cima de um site com defeito.
* Esvazie o seu banco de dados excluindo todas as tabelas ou crie um novo banco de dados e
atribua um usuário de banco de dados para ele.
* Exclua todos os diretórios e arquivos dentro do diretório raiz do seu Joomla.

## Akeeba Quickstart

Se você usou o Akeeba Backup, então use o Akeeba Quickstart para restaurar seu backup.
* Consulte o [Tutorial em Vídeo](http://akee.ba/abrestoreanywhere "").
* Baixe o Akeeba Quickstart (PDF 94Kb) gratuitamente.
* Verifique se o site restaurado funciona corretamente!

O Akeeba Quickstart restaura tanto o banco de dados quanto os arquivos do Joomla. Outros métodos restauram o banco de dados e os arquivos do Joomla separadamente.

## Restaurar o Banco de Dados

Se você tiver um backup do banco de dados, é melhor usar ferramentas do sistema para restaurá-lo. O *phpMyAdmin* pode instalar bancos de dados de tamanho moderado, mas pode ficar sem tempo ou memória em bancos de dados grandes.

Se você estiver usando cPanel em um serviço de hospedagem, pode importar um banco de dados na página de *Backup / Restore*. Isso não é descrito aqui.

Se você tiver acesso à linha de comando, seja em um serviço de hospedagem ou no seu computador local, laptop ou desktop, pode usar a linha de comando `mysql` para fazer a importação. Faça o upload do arquivo do banco de dados para um local temporário fora do seu diretório web e expanda-o para obter um arquivo com extensão `.sql`. Em seguida, use o seguinte comando:
```
mysql -u nomedeusuario -p -D nomedobanco < arquivo_dump.sql
```
Substitua `nomedeusuario`, `nomedobanco` e `arquivo_dump.sql` pelos valores reais para o seu site. Você poderá ser solicitado a inserir a senha do usuário do banco de dados. Pode levar algum tempo, mas deve ser concluído.

## Restaurar os Arquivos

Trata-se de uma questão simples de expandir o arquivo comprimido do seu último backup. Exceto que, às vezes, não é tão simples assim. Dependendo do seu sistema operacional e do método escolhido, os diretórios e arquivos arquivados podem aparecer todos no diretório atual ou em um novo diretório, ou você pode ser solicitado a indicar um diretório de destino. Até você saber o que seu sistema faz, pode ser melhor colocar o arquivo compactado em um diretório vazio, expandi-lo lá e, em seguida, mover o diretório contendo para onde precisar.

Alguns usuários preferem usar SFTP para fazer upload de arquivos para um serviço de hospedagem a partir dos arquivos do arquivo extraídos localmente. Há milhares de arquivos, então isso consome bastante tempo.

Na raiz do seu site, há um arquivo chamado `configuration.php`. Ele contém o nome do banco de dados e as credenciais de acesso. Certifique-se de que elas estejam corretas para seu site restaurado. O arquivo tem permissões de acesso definidas para 444. Isso precisa ser alterado para 644 para que você possa salvar qualquer edição necessária.

Se tudo correr bem, seu site restaurado deve funcionar e estar no estado em que estava quando o backup foi feito.

## Copiando um Site

Existem várias boas razões para copiar um site inteiro de um servidor para outro. Por exemplo, os especialistas do Fórum frequentemente recomendam que os usuários criem uma versão local de um site em um laptop ou computador de mesa para fins de teste, como experimentar novas extensões ou designs. Às vezes, uma pessoa decide mudar para um novo serviço de hospedagem por razões de custo ou desempenho.

Qualquer que seja o motivo, o processo é relativamente simples: faça um backup no site original e restaure-o no site de destino. Há algumas questões a serem observadas:

* Certifique-se de que o host de destino atenda aos Requisitos Técnicos Mínimos do Joomla. Isso geralmente significa versões de Servidor, PHP e Banco de Dados.
* Após a instalação, você pode descobrir que alguns módulos essenciais não foram habilitados. A maioria dos serviços de hospedagem corrigirá esses problemas mediante solicitação.

*Traduzido por openai.com*

