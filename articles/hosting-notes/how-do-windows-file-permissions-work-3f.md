<!-- Filename: How_do_Windows_file_permissions_work%3F / Display title: Permissões de Arquivos do Windows  -->

## Introdução

Para aqueles de vocês que estão desenvolvendo ou entregando seus sites Joomla! em um ambiente Windows, às vezes é difícil obter informações relevantes sobre permissões. Infelizmente, é um fato que a maioria dos serviços web são oferecidos sob Unix e que o Unix é bem documentado neste ambiente. Esperamos que as informações a seguir ajudem a esclarecer qualquer confusão e forneçam um pouco de orientação também.

### Visão Geral do Servidor Web Windows

Primeiramente, vamos discutir as diferenças entre servidores. Em geral, a maioria das pessoas que usa Windows parece estar usando Apache(Win32) ou Microsoft IIS. Esses dois servidores web operam de maneira muito diferente e utilizam modelos de entrega ligeiramente diferentes. O Apache(Win32) geralmente é executado no computador host como o Usuário sob o qual foi instalado, enquanto o IIS é instalado sob um usuário específico, mas será executado sob um novo usuário instalado *IUSR_*.

### Padrões de Permissão

Por padrão, o Unix tende a dar acesso total apenas ao usuário *proprietário* para arquivos e diretórios. Em oposição a essa abordagem, o Windows, por padrão, também atribuirá ao Grupo *Todos* permissões totais. A primeira coisa que qualquer bom Administrador de Windows fará é remover os direitos do grupo *Todos* para melhorar a segurança. Para testes em PC local, isso provavelmente não é necessário, mas explica por que, se *Todos* não for removido e você executar algum tipo de script de verificação de permissões ou a verificação pré-instalação do Joomla!, no geral você terá permissões totais de *Leitura, Escrita e Execução*, porque você está adquirindo os direitos do Grupo *Todos*.

### Servidor de Informações da Internet da Microsoft (IIS)

O IIS vem em dois sabores principais, PWS (Servidor Web Pessoal) e IIS (Servidor de Informações da Internet). Essencialmente, estas são a mesma aplicação. O PWS é apenas uma versão reduzida do IIS projetada para ambientes desktop, enquanto o IIS é projetado para ambientes de servidores. O PWS limita você a um único site principal, de modo que suas instalações de aplicativos geralmente estarão em subdiretórios do site principal. O IIS, por outro lado, oferece a funcionalidade para que Hosts Virtuais sejam executados desses diretórios, oferecendo capacidade multissite.

Devido às diferentes limitações de funcionalidade, o PWS não possui o *Assistente de Permissões* pois é determinado que não é necessário. Apenas um usuário usará o servidor PWS. No IIS, muitos usuários usarão o servidor, portanto, diferentes atribuições de permissão são necessárias.

Uma vez que a conta *Todos* é removida, o Windows IIS fica agora com a conta *IUSR_* tendo direitos de nível superior aos diretórios do Servidor Web. Uma verificação de permissões agora deve gerar resultados diferentes. Apenas a conta *IUSR_* tem permissões totais e outros usuários devem adquirir apenas *Leitura* ou nenhum direito. Os direitos são determinados por quais outros usuários foram atribuídos aos direitos dos diretórios IIS manualmente.

### Atribuindo Permissões

Atribuir permissões no Windows é bastante direto, mas pode ser um pouco confuso às vezes. Clique com o botão direito do mouse na pasta ou arquivo apropriado. Selecionar *Propriedades* ou *Compartilhamento e Segurança* abrirá o painel de Gerenciamento de Segurança do Windows. Selecionar (clique uma vez) qualquer nome de usuário listado exibirá os direitos que esse usuário possui na metade inferior do painel. Alguns direitos podem estar *acinzentados*. Estes não estão disponíveis, ou porque o usuário atual (com quem você está logado) não tem permissões altas o bastante para alterá-los, ou eles são herdados do diretório acima e foram configurados para usar as permissões desse diretório de nível superior (este é geralmente o mecanismo padrão).

Como você pode ver, o Windows utiliza o seguinte esquema de Permissões/Direitos:

| # | Permissões | Direitos |
|:-----:|:----------|:---------|
| 1 | Controle Total | Permite: 1, 2, 3, 4, 5, 6, 7 |
| 2 | Modificar | Permite: 2, 3, 4, 5, 6 |
| 3 | Ler & Executar | Permite: 3, 4 |
| 4 | Listar Conteúdo da Pasta | Permite: 4 (mas não pode executar programas) |
| 5 | Ler | Permite: 5 (Implica: 4) |
| 6 | Escrever | Permite: 6 (Implica:4) |
| 7 | Permissões Especiais | Permite: Combinações |

### Propriedades de permissões de arquivos do Windows

As permissões de arquivos do Windows podem ser vistas como tendo propriedades **semelhantes** às permissões de arquivos UNIX ou Linux (Modos), elas são apenas representadas de maneira diferente. Por exemplo, se você é principalmente um usuário de Unix/Linux, provavelmente está acostumado a ter permissões representadas como 644/666 755/777, em vez de serem descritas nos termos acima. Assim, quando você é citado para usar 644 isso equivale a:

* O proprietário deste arquivo pode ler e escrever nele.
* O grupo do proprietário pode ler o arquivo.
* Todas as outras pessoas podem ler o arquivo.

**Nota:** As permissões do Windows e Unix (Listas de Controle de Acesso) não se equacionam exatamente, pois o Windows não usa o mecanismo de *Grupos* da mesma maneira. No entanto, para esta discussão e no que diz respeito ao ambiente de hospedagem web, elas podem ser sumariamente equiparadas. Ah, mas, no Windows ***Grupos*** não são usados e ***Todos*** deveriam ter sido removidos. É aqui que Windows e Unix não se equiparam exatamente, mas o que pode ser feito é *corresponder* ou *correlacionar* significados equivalentes.

Este esboço não vai realmente fornecer a você um guia específico de permissões para Windows ou NTFS, mas mais um entendimento de como as permissões comumente citadas no estilo numerado UNIX/Linux se correlacionam em uma máquina com um sistema de arquivos NTFS. Os arquivos que são colocados na pasta raiz www ou public_html, ou qualquer diretório para o qual seu site (www.dominio.com.au ou localhost) aponte em seu disco rígido devem ser de propriedade de sua conta de usuário, mas apenas se esse usuário não for o que é considerado um usuário privilegiado como *Administrador* no Windows ou *root* no UNIX/Linux. Essas contas permitem acesso excessivo e nunca devem ser usadas para uso diário.

### Melhores Práticas

As práticas de segurança comumente usadas sugerem que todos os **arquivos** devem ter as seguintes permissões.

* **Proprietário:** Ler & Escrever
* **Grupo:** Apenas Leitura
* **Outros:** Apenas Leitura

Todos os **diretórios/pastas** devem ter as seguintes permissões:

* **Proprietário:** Ler, Escrever & Executar
* **Grupo:** Ler & Executar
* **Outros:** Ler & Executar

Argumentavelmente, isso não é necessariamente uma segurança *ideal*, mas um equilíbrio deve ser encontrado entre segurança, funcionalidade e manutenção. O Windows, ao contrário do Unix, não mantém um ACL único para *Executar*, mas simplesmente fornece *Ler & Executar* combinados, o que não implica *Escrever*. No entanto, o ACL de *Ler & Executar* implica *Listar Conteúdo do Diretório*. Portanto, se você tiver apenas permissões de *Ler & Escrever* em um diretório mas não *Executar* você não poderá ver o conteúdo do diretório e também poderá ter problemas ao tentar executar o arquivo através de um navegador web. É necessário um pouco de entendimento das permissões UNIX/Linux para realmente equipará-las/correlacioná-las com as permissões do Windows. A tabela a seguir deve ajudar:

| Modo Unix | ACL do Windows | Comentários |
|:-----:|:----------|:---------|
| 7 | Modificar | Ler, Escrever & Executar, você deve ser o proprietário deste arquivo |
| 6 | Ler & Escrever |  |
| 5 | Ler & Executar | usado para a maioria dos aplicativos |
| 4 | Apenas Ler | segurança por obscuridade não é uma boa prática |
| 3 | Escrever & Executar | não disponível no Windows, a menos que "Permissões Especiais" sejam usadas, não comumente usado |
| 2 | Apenas Escrever | não disponível no Windows, a menos que "Permissões Especiais" sejam usadas, não comumente usado |
| 1 | Apenas Executar | não disponível no Windows, a menos que "Permissões Especiais" sejam usadas, não comumente usado |

Em comparação aos Modos Unix, quando você vê algo como 644, você dividiria isso em três elementos:

**6**  :  **4**  : **4**

O primeiro número representa as permissões do **Proprietário**, o segundo representa as permissões do ***Grupo*** e o terceiro, as permissões dos ***Outros***. O equivalente no Windows seria:

* **Proprietário** (6) : **Ler & Escrever**
* **Grupo** (4) : **Apenas Leitura**
* **Outros** (4) : **Apenas Leitura**

Esperamos que este exemplo ofereça algum insight sobre como correlacionar Modos/Permissões Unix com Permissões/ACLs do Windows. Este documento não inclui assuntos mais complexos, tais como permissões *Efetivas*, *Herdadas*, ou *Especiais*. Apesar da facilidade de uso do Windows, os mecanismos de Permissões e ACL da Microsoft são, na verdade, razoavelmente complexos e muito extensivos, mas isto pode apenas fornecer uma referência rápida para tentar aliviar parte da confusão em torno das traduções de Permissões entre Unix e Windows.

*Traduzido por openai.com*

