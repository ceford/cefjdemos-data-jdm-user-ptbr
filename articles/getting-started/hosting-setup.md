<!-- Filename: J4.x:Hosting_Setup / Display title: Configuração de Hospedagem -->

## Introdução

Esta página oferece algumas orientações para quem é totalmente novo em tecnologia de hospedagem. Você pode configurar um site no seu próprio laptop ou computador desktop. Isso é conhecido como hospedagem local e é uma boa maneira de experimentar novos recursos, além de ser completamente gratuito. Para tornar o conteúdo do seu site disponível para o resto do mundo, você precisará de uma conta em um serviço de hospedagem, e para isso você terá que pagar.

## Software de Suporte

Joomla! é uma aplicação que depende de três itens de software de suporte:
a linguagem de script PHP, um banco de dados (um dos MySQL, MariaDB ou PostgreSQL)
e um servidor web (um dos Apache, Nginx, Microsoft IIS, ou ...). Os números
mínimos de versão estão indicados nas tabelas a seguir:

### Requisitos para Joomla! 5.x

| Software           | Recomendado     | Mínimo      |
|--------------------|-----------------|-------------|
| PHP                | 8.3             | 8.1.0       |
| **Bancos de Dados**|                 |             |
| MySQL              | 8.1             | 8.0.13      |
| MariaDB            | 11.1.0          | 10.4.0      |
| PostgreSQL         | 16.0            | 12.0        |
| **Servidores Web** |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.25            | 1.21        |
| Microsoft IIS      | 10              | 10          |

### Requisitos para Joomla! 4.x

| Software           | Recomendado     | Mínimo      |
|--------------------|-----------------|-------------|
| PHP                | 8.2             | 7.2.5       |
| **Bancos de Dados**|                 |             |
| MySQL              | 8.0             | 5.6         |
| PostgreSQL         | 11.0            | 11.0        |
| **Servidores Web** |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.18            | 1.10        |
| Microsoft IIS      | 10              | 8           |

## Serviços de Hospedagem

Os serviços de hospedagem comercial oferecem tudo que você precisa para suportar um site. Alguns também oferecem instalação com um clique de aplicativos populares, como Sistemas de Gerenciamento de Conteúdo, Fóruns, Wikis, e assim por diante. Mas, por favor, note: os experts do Fórum do Joomla não recomendam o uso da instalação com um clique do Joomla.

Cada serviço de hospedagem oferece diferentes planos em diferentes níveis de preço. Quanto mais você pagar, mais espaço em disco e largura de banda você receberá, junto com mais endereços de email, bancos de dados, e assim por diante. Alguns também fornecem um nome de domínio gratuito. Na maioria das vezes, você terá que pagar por um nome de domínio e uma pequena taxa de registro anual.

## Hospedagem Gratuita

Não existe hospedagem realmente gratuita! Entretanto, um serviço de hospedagem parceiro do Joomla oferece um site Joomla gratuito no domínio joomla.com. Isso lhe dá a oportunidade de experimentar seu próprio site Joomla totalmente funcional sem nenhum custo. É semelhante a um plano de hospedagem compartilhada, mas com restrições e frequentes solicitações para atualizar para um plano pago. Além disso, o plano gratuito precisa ser renovado a cada 30 dias ou será encerrado. O artigo a seguir mostra os passos necessários para configurar um site Joomla gratuito.

* [Hospedagem Joomla Gratuita](jdocmanual?article=user/hosting/free-hosting)

Se você descobrir que gosta do Joomla, pode atualizar para um plano pago ou procurar outro serviço de hospedagem que atenda às suas necessidades e orçamento.

## Hospedagem Compartilhada

Você pode obter um plano de hospedagem mínimo por cerca de £/$/€50 por ano. Este nível de plano
é frequentemente referido como hospedagem compartilhada e é adequado para
qualquer coisa que não envolva dados sensíveis. As empresas devem procurar aconselhamento especializado
sobre planos de hospedagem adequados. Escolher um serviço de hospedagem não está
isento de problemas. O mais barato pode ter configurações de *php.ini*
indebidamente restritivas que não aparecem na publicidade deles. Alguns podem ter uma
reputação ruim em suporte.

Se você optar por um plano de hospedagem compartilhada, verifique o seguinte:

- Suporte para aplicativos PHP como Joomla, WordPress e Mediawiki.
- Espaço em disco: 500Mb é um mínimo absoluto. 1Gb ou mais seria melhor
  se você planeja usar muitas imagens.
- Número de bancos de dados: o Joomla utiliza um, mas você logo perceberá que precisa de 5
  ou 10 ou mais. Alguns planos oferecem um número ilimitado dentro da alocação total
  de espaço em disco.
- Tamanho do banco de dados: com a Pesquisa Inteligente, o banco de dados pode crescer muito rapidamente.
  Se a hospedagem compartilhada tiver uma restrição no tamanho do banco de dados,
  será importante descobrir qual é essa restrição. Isso pode levar a um site
  não funcionar.
- Número de endereços de e-mail: bastante!
- Número de conexões HTTP e DB ao servidor, que alguns hosts
  compartilhados limitam.
- Backups: como são feitos e há um documento de Termos de Serviço (TOS)
  indicando quem é o responsável pelos backups.

Verifique também o painel de controle e a plataforma oferecida. A julgar pelas postagens
no Fórum, a maioria usa cPanel em Linux. O serviço de hospedagem deve fornecer todo
o software básico de suporte ao site:

- Servidor web Apache 2.4+ - *índices de diretórios* devem ser desativados. Também suportado:
  - Nginx 1.18+ (menos usuários, portanto menos suporte no Fórum)
  - Microsoft IIS\[6\] (menos usuários, portanto menos suporte no Fórum)
- Banco de dados MySQLi 8.1+ ou clone MariaDB com suporte a InnoDB. Também suportado:
  - PostgreSQL 11.0+ (menos usuários, portanto menos suporte no Fórum).
- Recomenda-se PHP 8+.
- Ferramenta de gerenciamento de banco de dados phpMyAdmin.

Antes de comprar, verifique os seguintes requisitos mínimos de PHP para o Joomla:

- *memory_limit* - Mínimo: 256M
- *upload_max_filesize* - Mínimo: 64M
- *post_max_size* - Mínimo: 64M
- *max_execution_time* - Recomendado: 30
- *allow_url_fopen* - true

Muitos desses parâmetros podem ser definidos pelo usuário no cPanel. Pergunte se é
possível.

Se você comprou um nome de domínio, seu serviço de hospedagem o configurará
para você. Eles também devem fornecer um endereço IP para usar até que
o registro do seu domínio se propague para os Servidores de Nome de Domínio (DNS),
geralmente em algumas horas.

O artigo a seguir mostra o que esperar se você adquirir um plano de hospedagem que
inclua uma interface de usuário cPanel.

* [Hospedagem cPanel](jdocmanual?article=user/hosting/cpanel-hosting)

## Hospedagem VPS

Um plano de hospedagem em Servidor Virtual Privado (VPS) oferece acesso total a um servidor que compartilha hardware. Ele se comporta como um computador dedicado. Você pode parar e iniciar o servidor, reiniciá-lo e instalar seu próprio software exatamente como faria em um computador de mesa. Você pode criar contas para usuários individuais, assim como na hospedagem compartilhada. Tipicamente, você pode permitir alguns recursos que normalmente não são permitidos em contas de hospedagem compartilhada.

Planos de hospedagem Dedicada e em Nuvem são semelhantes em princípio, mas oferecem recursos dedicados ou recursos adaptados às suas necessidades.

Esses planos avançados não são abordados aqui.


## Hospedagem Local

A maioria das pessoas que desenvolve websites mantém cópias locais em um laptop ou computador de mesa para testar atualizações ou novas extensões ou para experimentar novos designs. Configurar um site de desenvolvimento local exige algum conhecimento técnico, mas é relativamente fácil seguir instruções simples.

Os artigos a seguir descrevem como configurar hospedagem local em diferentes tipos de computadores de mesa ou laptop:

* [Hospedagem Local no Windows](jdocmanual?article=user/hosting/local-hosting-on-windows) apenas para Windows
* [Hospedagem Local com XAMPP](jdocmanual?article=user/hosting/local-hosting-with-xampp) para Linux, Mac e Windows.
* [Hospedagem Local no Linux](jdocmanual?article=user/hosting/local-hosting-on-linux)

