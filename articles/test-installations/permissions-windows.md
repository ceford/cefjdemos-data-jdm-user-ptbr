<!-- Filename: How_do_Windows_file_permissions_work? / Display title: Permissões de Arquivo: Windows -->

## Introdução

Para aqueles que estão desenvolvendo ou entregando seus sites Joomla! a partir de um ambiente Windows, às vezes é difícil obter informações relevantes sobre permissões. Infelizmente, é fato que a maioria dos serviços de hospedagem Web é oferecida sob Unix e que o Unix é bastante bem documentado nesse ambiente. Esperamos que as informações a seguir ajudem a esclarecer qualquer confusão e ofereçam um pouco de orientação também.

## Visão Geral dos Servidores Web Windows

Primeiro, vamos discutir as diferenças entre servidores. Em geral, a maioria dos usuários de Windows parece estar utilizando o Apache (Win32) ou o Microsoft IIS. Esses dois servidores web operam de maneira muito diferente e utilizam modelos de entrega ligeiramente distintos. O Apache (Win32) geralmente é executado no computador hospedeiro como o Usuário sob o qual foi instalado, enquanto o IIS é instalado sob um usuário específico, mas será executado sob um usuário recém-instalado *IUSR_*. 

## Padrões de Permissão

Por padrão, o Unix tende a dar acesso total aos arquivos e diretórios apenas para o usuário *proprietário*. Em contraste, o Windows, por padrão, também atribui permissões totais ao grupo *Todos*. A primeira coisa que qualquer bom Administrador do Windows faz é remover os direitos do grupo *Todos* para melhorar a segurança. Para testes em PCs locais, isso provavelmente não é necessário, mas explica por que, se *Todos* não for removido e você executar algum tipo de script de verificação de permissões ou a verificação de pré-instalação do Joomla!, você terá permissões completas de *Leitura, Escrita e Execução*. Você está adquirindo os direitos do grupo *Todos*. 

## Servidor de Informações da Internet da Microsoft (IIS)

O IIS vem em dois principais formatos: PWS (Personal WebServer) e IIS (Internet Information Server). Essencialmente, são o mesmo aplicativo. O PWS é apenas uma versão reduzida do IIS projetada para ambientes de desktop, enquanto o IIS é projetado para ambientes de servidor. O PWS limita você a um único site principal, então as instalações de seu aplicativo estarão geralmente em subdiretórios do site principal. O IIS, por outro lado, fornece a funcionalidade para Hosts Virtuais serem executados a partir destes diretórios, oferecendo capacidade multissite.

Devido às diferentes limitações de funcionalidade, o PWS não possui o *Assistente de Permissões*, pois é considerado desnecessário. Somente um usuário utilizará o Servidor PWS. No IIS, muitos usuários usarão o Servidor, portanto diferentes atribuições de permissão são necessárias.

Uma vez que a conta *Todos* é removida, o Windows IIS fica agora com a conta *IUSR_*** com direitos de nível superior aos diretórios do Servidor Web. Uma verificação de permissões agora deve fornecer resultados diferentes. Somente a conta *IUSR_*** possui permissões completas, e outros usuários devem obter ou *Somente Leitura* ou nenhum direito. Os direitos são determinados por quais outros usuários foram atribuídos manualmente aos diretórios IIS.

### Atribuindo Permissões

Atribuir permissões no Windows é razoavelmente direto, mas pode ser um pouco confuso às vezes. Clique com o botão direito no arquivo ou pasta apropriado. Selecionar *Propriedades* ou *Compartilhamento e Segurança* levará ao painel de Gerenciamento de Segurança do Windows. Selecionar (clicar uma vez) qualquer nome de usuário listado exibirá os direitos que esse usuário possui na metade inferior do painel. Alguns direitos podem estar *acinzentados*. Estes não estão disponíveis, ou porque o usuário atual (com o qual você está logado) não possui permissões suficientes para alterá-los, ou porque são herdados do diretório acima e foram configurados para usar as permissões daquele diretório de nível superior. (Este geralmente é o mecanismo padrão.)

Como você pode ver, o Windows utiliza o seguinte esquema de Permissões/Direitos:

| # | Controle | Permissões #     |
| :---:        |:----   | :--- |
| 1.|  Controle Total | Permite: 1, 2, 3, 4, 5, 6, 7 |
| 2.| Modificar | Permite: 2, 3, 4, 5, 6 |- |
| 3.| Ler & Executar | Permite: 3, 4  |- | 
| 4.| Listar Conteúdo da Pasta | Permite: 4 (mas não pode executar programas)  |- |
| 5.| Ler | Permite: 5 (Implica: 4) |- |
| 6.| Gravar | Permite: 6 (Implica:4 ) |- |
| 7.| Permissões Especiais | Permite: Combinações |

### Propriedades de permissões de arquivos do Windows

As permissões de arquivos do Windows podem ser vistas como tendo propriedades semelhantes às permissões de arquivos (Modos) de UNIX ou Linux. Elas apenas são representadas de maneira diferente. Por exemplo, se você é principalmente um usuário de Unix/Linux, é provável que esteja acostumado a ter permissões representadas como 644/666 755/777, em vez de serem descritas nos termos acima. Portanto, quando você usa 644, isso significa:

- O proprietário deste arquivo pode ler e escrever nele.
- O grupo do proprietário pode ler o arquivo.
- Todos os outros podem ler o arquivo.

**Nota:** As permissões do Windows e do Unix (Listas de Controle de Acesso) não são exatamente iguais; o Windows não usa o mecanismo de *Grupos* da mesma maneira. Para esta discussão e em relação ao ambiente de hospedagem web, elas podem ser equiparadas. Ah, mas no Windows, os *Grupos* não são usados e o *Todos* já deve ter sido removido. É aqui que o Windows e o Unix não são exatamente iguais, mas o que pode ser feito é *igualar* ou *correlacionar* significados equivalentes.

Este esboço não irá fornecer realmente um guia específico de permissões Windows ou NTFS, mas mais um entendimento de como as permissões numéricas comuns em estilo UNIX/Linux correlacionam-se em uma máquina com um sistema de arquivos NTFS. Os arquivos que são colocados na pasta raiz `www` ou `public_html`, ou em qualquer diretório que seu site (`www.dominio.com` ou `localhost`) aponte no seu disco rígido, devem ser de propriedade da sua conta de usuário, mas somente se esse usuário não for considerado um usuário privilegiado, como *Administrador* no Windows ou *root* no UNIX/Linux. Essas contas permitem muito acesso e nunca devem ser usadas para uso diário.

### Práticas Recomendadas

As práticas comuns de segurança sugerem que todos os **arquivos** devem ter as seguintes permissões.

- **Proprietário** Ler & Escrever
- **Grupo** Somente Leitura
- **Outros** Somente Leitura

Todos os **diretórios/pastas** devem ter as seguintes permissões.

- **Proprietário** Ler, Escrever & Executar
- **Grupo** Ler & Executar
- **Outros** Ler & Executar

Pode-se argumentar que isso não é necessariamente segurança *ótima*, mas um equilíbrio deve ser alcançado entre segurança, funcionalidade e manutenção.

O Windows, ao contrário do Unix, não mantém uma ACL única para *Executar*, mas simplesmente fornece *Ler & Executar* combinados, o que não implica *Gravar*. O ACL *Ler & Executar* no entanto implica em *Listar Conteúdos do Diretório*. Portanto, se você tiver apenas permissões *Ler & Gravar* em um diretório, mas não *Executar*, não poderá ver o conteúdo do diretório e também poderá ter problemas ao tentar rodar o arquivo através de um navegador da web. Um pequeno entendimento das permissões UNIX/Linux é necessário para equipará-las/correlacioná-las totalmente às permissões do Windows. A tabela a seguir deve ajudar:

| Modo Unix   | ACL do Windows | Comentários|
|:-----------:| :----   | :--- |
| 7 | Modificar| Ler, Gravar & Executar, você deve ser o proprietário deste arquivo | 
| 6 | Ler & Gravar | | 
| 5 | Ler & Executar| usado na maioria das aplicações | 
| 4 | Somente Leitura | segurança por obscuridade não é uma boa prática | 
| 3 | Gravar & Executar | não disponível no Windows, a menos que Permissões *Especiais* sejam usadas, não é comumente usado | 
| 2 | Somente Gravar | não disponível no Windows, a menos que Permissões *Especiais* sejam usadas, não é comumente usado | 
| 1 | Somente Executar | (não disponível no Windows, a menos que Permissões *Especiais* sejam usadas, não é comumente usado) |

Em comparação aos modos Unix, quando você vê algo como 644, divida em três elementos:

O primeiro número representa as permissões do Proprietário, o segundo representa as permissões do Grupo e o terceiro, as permissões dos Outros. O equivalente no Windows seria: 

- **Proprietário** (6) Ler & Gravar
- **Grupo** (4) Somente Leitura
- **Outros** (4) Somente Leitura

Espero que este exemplo forneça alguma visão sobre como correlacionar Modos/Permissões Unix para Permissões/ACLs do Windows. Este documento não inclui assuntos mais complexos, como permissões *Efetivas*, *Herdadas* ou *Especiais*. Apesar da facilidade de uso do Windows, os mecanismos de Permissões e ACLs da Microsoft são realmente razoavelmente complexos e muito extensos, mas isso pode lhe dar uma referência rápida para tentar amenizar um pouco da confusão em torno das traduções de Permissões Unix e Windows.

*Traduzido por openai.com*

