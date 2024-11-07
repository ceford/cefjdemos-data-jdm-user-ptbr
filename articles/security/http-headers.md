<!-- Filename: https://magazine.joomla.org/all-issues/may-2022/joomla-new-http-headers-plugin-for-j4 / Display title: Cabeçalhos HTTP -->

## Artigo de Revista

Este artigo é baseado em um artigo da Joomla! Community Magazine por Brendan Hedges
na edição de maio de 2022.

Embora escrito para Joomla 4, o conteúdo se aplica igualmente ao Joomla 5.

## Novo Plugin de Cabeçalhos HTTP do Joomla Para J4

Dando continuidade ao artigo do mês passado sobre segurança, senhas e o plugin WebAuthn do Joomla, este mês vamos analisar outra funcionalidade de segurança do Joomla que foi lançada com o J4. Trata-se do plugin de Cabeçalhos HTTP, que agora está incluído como parte das funções principais do Joomla.

A internet está sempre se desenvolvendo, e o Joomla nunca fica muito atrás. É por isso que eu o escolho como minha plataforma de desenvolvimento web preferida. Não importa se o seu site é um pequeno site familiar ou uma plataforma de comércio eletrônico totalmente desenvolvida com milhões em vendas, o framework Joomla tem algo para todos e está sempre procurando implementar novas tecnologias. Algumas são até inovadoras.

> A introdução do plugin de Cabeçalhos HTTP no núcleo do Joomla 4 é um grande passo à frente para ajudar a proteger seu site contra ataques e atividades maliciosas.

Este plugin de segurança do sistema ajuda os proprietários de sites a configurar facilmente os Cabeçalhos de Segurança HTTP a partir do backend familiar do Joomla, em vez de ter que vasculhar o arquivo htaccess ou outros arquivos de configuração. Ou, pior ainda, seu Cpanel de hospedagem na web.

Veja como é complicado configurar isso no Cpanel e me diga que você não cometerá um erro! E isso tudo assumindo que, uma vez que o framework está instalado no Apache e diretórios criados, você sabe o formato correto para adicionar os cabeçalhos HTTP que deseja integrar.

Quantas vezes você tentou implementar um comando htaccess apenas para recarregar seu site e, em seguida, enfrentar um erro http500?

O maior problema é que, se você não acertar o formato do seu Cabeçalho HTTP, você irá quebrar seu site.

Mesmo assim, o que funciona para um site pode não funcionar para outro. Um bom exemplo disso é o meu arquivo htaccess e a forma como configurava o navegador para carregar uma versão não www e https do meu site:
```
##www para não www e http para https mixin
RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} ^www\. [NC]
RewriteRule ^ https://meusite.com.br%{REQUEST_URI} [R=301,L,NE]
##Fim www para não www e http para https mixin
```

Isso funcionou muito bem para minha empresa de hospedagem anterior. Mas quando mudei para um host diferente, parou de funcionar. Vai entender!

O código htaccess que agora preciso usar para obter o mesmo resultado parece assim:
```
##www para não www e http para https mixin
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=301,L]
RewriteCond %{ENV:HTTPS} !on
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
##Fim www para não www e http para https mixin
```

Confuso, certo? E, se você cometer um único erro na formatação, BAM! Você quebrou seu site! Bem, pelo menos até você corrigir seu código.

É por isso que manter as coisas simples, como parte do núcleo do Joomla, significa menos frustração, menos tempo perdido procurando seus erros no Google e mais tempo para comemorar enquanto você se senta em sua cadeira e admira seu novo site.

Então, vamos ver o que realmente são os cabeçalhos HTTP, como você pode encontrar o plugin e o que pode fazer com eles. Vale a pena mencionar aqui que essa função do Joomla é uma função avançada, mais adequada para sites sensíveis a dados, ao invés do novo site que você criou com carinho sobre seus gatinhos fofos. No entanto, ao dizer isso, mesmo sites simples devem ser o mais seguros possível para impedir a execução de código malicioso após ter seu site invadido.

## O que são Cabeçalhos HTTP?

Os cabeçalhos HTTP não devem ser confundidos com a seção &lt;head&gt; do seu documento HTML. Eles são completamente diferentes. Cabeçalhos HTTP são o preâmbulo entre seu servidor web e o navegador. Um conjunto de instruções que informa ao navegador o que, ou mais importante, o que não exibir ao visitante.

Você pode visualizar os Cabeçalhos HTTP e como eles se referem a objetos HTML individuais nas Ferramentas de Desenvolvedor (DEV Tools) do seu navegador. No Google Chrome, abra as Ferramentas de Desenvolvedor e, em seguida, a aba Rede (Network). Agora, atualize a página web e clique em um item HTML no painel esquerdo. Ele exibirá o Cabeçalho HTTP para aquele item no painel direito.

Você pode ver na imagem abaixo que a imagem destacada está retornando um status HTTP de 200, então o navegador a encontrou. Há também uma gama de outras informações ligadas a esse item, como o tamanho do arquivo e as datas de edição.

![Cabeçalhos http do Joomla 1](../../../en/images/security/http-headers-dev-tools-headers.png)

Se um dos seus itens HTML falhar em exibir, você também pode obter uma pista sobre o motivo nos cabeçalhos HTTP. Neste exemplo, a segunda imagem falhou em exibir e você pode ver que, a partir das informações exibidas no painel direito, não há informações de Cabeçalho HTTP.

Exceto pela mensagem enigmática:

**Política de Referência:** 'strict-origin-when-cross-origin'

'Strict-origin-when-cross-origin' simplesmente significa que, quando um item HTML (uma imagem, neste caso) é servido de uma fonte diferente (não do seu servidor), então a política de cabeçalho HTTP definida naquele momento deve ser seguida. Neste exemplo, os Cabeçalhos HTTP, conforme definidos no plugin do Joomla, vão rejeitar todas as imagens que não se originarem deste site ou de um site diferente que esteja especificamente 'incluído' nos parâmetros de Cabeçalho HTTP configurados no plugin de cabeçalho HTTP do Joomla.

Assim, quando a imagem é chamada do documento HTML, o navegador a rejeita e ela não é carregada.

![Cabeçalhos http do Joomla 2](../../../en/images/security/http-headers-dev-tools-headers-reject.png)

O que difere de não ser encontrada e retornar uma mensagem de erro HTTP 404 não encontrado. Nesta situação, ainda está se tentando encontrar a imagem no servidor que a hospeda, mas o navegador não a encontrou.

![Cabeçalhos http do Joomla 3](../../../en/images/security/http-headers-dev-tools-headers-not-found.png)

## O que o Plugin de Cabeçalhos HTTP do Joomla faz

Além de informar ao navegador o que mostrar e retornar informações gerais sobre o documento HTML, os Cabeçalhos HTTP ajudam a mitigar ataques e vulnerabilidades de segurança que você possa ter no seu site Joomla. É aí que o plugin de Cabeçalhos HTTP do Joomla entra em ação. Ele faz isso ao exibir explicitamente o conteúdo HTML com base nas suas configurações no próprio plugin de Cabeçalhos HTTP do Joomla.

Ao adicionar cabeçalhos HTTP baseados em segurança extra ao seu site Joomla usando o plugin de Cabeçalhos HTTP, você estará fornecendo mais uma camada de segurança ao seu site Joomla.

Isso é importante porque, por padrão, uma página da web em HTML exibirá todo o seu conteúdo para o visitante, seja bom ou ruim. Isso a menos que seja explicitamente orientado para não fazê-lo nos cabeçalhos HTTP da página web. O plugin faz isso permitindo que você configure as opções avançadas de segurança disponíveis na Política de Segurança de Conteúdo para o seu site. O plugin pode ser configurado de forma diferente para cada site, dependendo das suas necessidades, tornando-se assim uma arma verdadeiramente flexível no seu arsenal contra hackers.

## Por que eu preciso deste plugin?

Em um mundo ideal, você não precisaria. No entanto, no mundo em que vivemos, há muitas pessoas inescrupulosas tentando encontrar maneiras de ganhar dinheiro às custas dos inocentes e desavisados. No nosso mundo, chamamos essas pessoas de hackers. Hackers se esforçam para explorar vulnerabilidades em softwares para ganho monetário, muitas vezes em detrimento do proprietário do site.

Usando o plugin HTTP Header do Joomla para controlar que conteúdo está sendo servido para seus visitantes, você reduz as chances de hackers conseguirem servir conteúdo malicioso do site para seus visitantes através de plugins desatualizados e vulneráveis. O que ajuda a impedir injeções de scripts maliciosos em seu site.

**Então, vamos pensar sobre esta situação hipotética por um minuto.**

Você tem um belo site Joomla 3. Foi feito há 5 anos e ainda parece e funciona perfeitamente. Todos os seus componentes, plugins e módulos estão atualizados. Perfeito, certo?

Bem, não exatamente, porque quando você fez seu site há 5 anos, instalou o moderno Plugin Foo Bar para imprimir "FOO BAR" na sua página inicial. Pareceu legal no começo, mas depois de um tempo você mudou de ideia e deletou o código de atalho do plugin {foo}FOO - BAR{/bar} do seu artigo na página inicial.

Mas, aqui está o problema: você não despublicou ou desinstalou o plugin em si e seu uso foi esquecido. **Isso é algo que TODOS nós somos culpados de fazer, tenho certeza.**

Pulando para hoje, 5 anos depois, aquele plugin ainda está lá, publicado e ativo em seu site, mas não foi atualizado por 5 anos porque você há muito tempo esqueceu do plugin, ou o autor parou de suportá-lo. Agora, algum sujeito nefasto percebeu que este plugin tem uma vulnerabilidade de segurança que pode ser explorada para iniciar um ataque de **Cross Site Scripting (XSS)** em seu site e fazer de seus visitantes desavisados, vítimas.

Cross-site scripting, que também é conhecido como XSS, é uma vulnerabilidade de segurança em seu site que permite a um atacante comprometer as interações que seus usuários têm com seu site agora vulnerável.

O atacante/hacker usa XSS para explorar seu site vulnerável para enviar um script malicioso para seu usuário desavisado. Como o script vem de seu site, o navegador do usuário não sabe ou suspeita que o script não deveria ser confiável e executa o script quando a página da web carrega e abre.

Scripts maliciosos executados desta maneira podem causar muitos problemas ao seu usuário, desde roubar senhas de login e dados de nomes de usuário mantidos em cookies, até enviar seu usuário para sites falsos de phishing. Scripts podem até mesmo alterar a aparência da página da web que seu site está servindo e mostrar diferentes anúncios.

Usar o **plugin HTTP Headers do Joomla** ajuda a parar o cross-site scripting garantindo que apenas os scripts e conteúdos que você deseja servir ao seu visitante sejam realmente servidos. Todo o resto é bloqueado.

Então, no exemplo acima, você poderia ter configurado o plugin HTTP Headers para servir apenas os arquivos JavaScript (script) do seu site a partir de uma pasta especificada, ou talvez um CDN se você usar um, para impedir o ataque.

Você também poderia impedir que o site executasse JavaScript embutido que está incorporado no HTML. Mas, esteja ciente de que dependendo de como você projetou o HTML do seu site, isso pode causar problemas mais adiante.

Isso ajudaria a impedir que códigos JavaScript maliciosos fossem executados em seu site. Mesmo que seu vulnerável Plugin Foo Bar fosse responsável por um hacker conseguir injetar código malicioso em seu site desde o início.

**Nota:**

> Pontos fracos comuns em sites que são propensos a ataques XSS são formulários de entrada de usuário (páginas de login de usuários, formulários de inscrição em newsletters, formulários de contato, etc.) sem validação e criptografia.

## Onde está o Plugin de Cabeçalhos HTTP?

Você pode encontrar o plugin de Cabeçalhos HTTP do Joomla juntamente com todos os outros plugins do Joomla, e ele é acessado da mesma forma que você está acostumado a fazer.

![Joomla cabeçalhos http 4](../../../en/images/security/http-headers-plugins.png)

## Usando o Plugin de Cabeçalhos HTTP

Usar o Plugin de HTTP do Joomla é relativamente simples, embora possa ser uma boa ideia se familiarizar com alguns dos termos especiais relacionados ao seu uso antes de fazer alterações nas configurações padrão. Embora, ao dizer isso, alguns deles já devem ser familiares para você.

**Por exemplo:**

Ao lidar com imagens, você verá o termo 'img-src', onde 'img' se refere a imagens e 'src' à fonte válida da imagem. Esses são termos com os quais já estamos familiarizados no HTML básico.

No final deste artigo, há uma lista de sites úteis com informações adicionais para ajudá-lo a usar este plugin do Joomla.

## Configurações do Plugin de Cabeçalhos HTTP - Aba 1

Ao abrir o plugin, a primeira aba exibida são as configurações básicas do plugin. Aqui, você pode ajustar as opções X-Frame, a política de referenciador (Referrer-Policy), a política de abertura entre origens (Cross-Origin-Opener-Policy) e também Forçar Cabeçalhos HTTP. Há também links com mais informações para ajudar você a entender melhor o que cada item faz.

**Vamos examinar cada um deles em detalhes.**

![Joomla http headers 5](../../../en/images/security/http-headers-plugins-tab-plugin.png)

### Opções X-Frame

A primeira configuração é para as Opções X-Frame. **Ela está ativada por padrão.**

Essa opção permite decidir se o conteúdo do seu site pode ser exibido em outro site em uma tag &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; ou &lt;object&gt;. Se você desativar esta opção, qualquer outro site poderá exibir seu site em um iframe.

Quando ativado, uma tag ‘x-frame-options: SAMEORIGIN’ é adicionada aos cabeçalhos do seu site. Essa tag permite que você exiba seu próprio conteúdo em uma tag &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; ou &lt;object&gt; no seu próprio site, mas impede que outros exibam seu conteúdo em um iframe em outro site.

![Joomla http headers 6](../../../en/images/security/http-headers-plugins-headers.png)

O cabeçalho X-Frame Options ajuda a proteger seu site e usuários contra ataques de **‘Click Jacking’**. Este ataque acontece quando um invasor coloca um &lt;iframe&gt; em seu próprio site com a origem configurada para o seu site e usa várias camadas transparentes para enganar o usuário, fazendo-o clicar em uma camada superior acreditando que está clicando em um link ou botão abaixo.

Isso permite ao invasor **“sequestrar”** cliques destinados à página original em um iframe e redirecioná-los para uma página diferente.

Práticas semelhantes podem ser usadas para registrar teclas digitadas, como detalhes de login e senha de contas de e-mail, redes sociais e até contas bancárias.

A maioria dos navegadores modernos suporta as Opções X-Frame, o que é excelente. Recomendo habilitar esta configuração no plugin de cabeçalhos HTTP para ajudar a proteger seus usuários contra ataques de Click Jacking.

**A maioria dos navegadores modernos suporta as Opções X-Frame.**

![Suporte de navegador a cabeçalhos HTTP](../../../en/images/security/http-headers-plugins-xframe-browser-support.png)

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Dica

Ative esta opção para restringir globalmente o que pode ser feito com &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; ou &lt;object&gt; em seu site. Para adicionar exceções, use ‘Forçar Cabeçalhos HTTP’ para aplicar exceções granulares.
</div>

### Política de Referenciador (Referrer-Policy)

O próximo item na lista da primeira aba é a **Política de Referenciador**. Quando ativada, esta configuração permite escolher o quanto de dados do seu site potencialmente será transferido para outro site caso um link ou outro objeto HTML seja clicado.

Essa política é comum em tags HTML &lt;a&gt;, onde você pode formatar um link como &lt;a href=”https://someplace.com” rel=”noreferrer”&gt;Clique Aqui&lt;/a&gt;. A tag noreferrer mantém em segredo os detalhes da página de origem ao remover a informação de referência do cabeçalho HTTP.

Ter consciência dos dados que seu site pode ‘vazar’ para outro site ao qual você cria links é importante para a segurança de seu site e de seus usuários.

Isso é particularmente relevante se o site permite registros de usuários, contém dados sensíveis ou processa transações financeiras. O plugin de cabeçalhos HTTP do Joomla ajuda a controlar isso globalmente, em vez de ser definido para cada link individual.

Por padrão, a Política de Referenciador do seu site é configurada como ‘strict-origin-when-cross-origin’. Isso não bloqueia nenhum dado de referenciador da página de origem, a menos que seja enviado para uma página http menos segura. Como a maioria das páginas usa https hoje em dia, esse problema se torna maior do que costumava ser.

![Joomla http headers 8](../../../en/images/security/http-headers-plugins-headers-referer-policy.png)

Existem, claro, muitos usos inofensivos desses dados ‘vazados’ quando uma Política de Referenciador não é estabelecida para seu site. Isso pode incluir a coleta de dados para análise, logs ou caching otimizado.

Infelizmente, nem todos os sites para os quais você cria links utilizam esses dados de maneira inofensiva. Veja a situação a seguir como exemplo.

A maioria dos sites que permite registro de usuários terá um link de redefinição de senha ao lado do formulário de login. É provável que a página também contenha links externos, redes sociais ou links ‘úteis’ no rodapé.

Se não houver uma Política de Referenciador, é possível que o cabeçalho de Referenciador enviado para um desses sites externos ao clicar em um link contenha o link de redefinição de senha, entre outras informações compartilhadas.

Isso pode representar um risco de segurança, comprometendo dados do usuário.

Devido a esse risco em páginas com dados sensíveis, é bom evitar conteúdo de terceiros, incluindo links e conteúdo em &lt;iframes&gt;, como widgets de redes sociais e vídeos do YouTube. Dados inseridos nessas páginas poderiam ser enviados pelo cabeçalho de Referenciador para outros sites.

O plugin de cabeçalhos HTTP do Joomla permite escolher uma entre 8 Políticas de Referenciador, cada uma com diferentes limites de dados a serem compartilhados.

![Joomla http headers 9](../../../en/images/security/http-headers-plugins-headers-referer-policy-setting.png)

Vamos examinar essas opções, descritas no site da Mozilla:

* **no-referrer**<br>
    O cabeçalho de Referenciador será omitido: as requisições enviadas não incluirão informações de referência.
* **no-referrer-when-downgrade**<br>
    Envia a origem, caminho e query string no cabeçalho de Referenciador quando o nível de segurança do protocolo permanece igual ou melhora (HTTP→HTTP, HTTP→HTTPS, HTTPS→HTTPS). Não envia o cabeçalho para destinos menos seguros (HTTPS→HTTP, HTTPS→arquivo).
* **origin**<br>
    Envia apenas a origem no cabeçalho de Referenciador.
* **origin-when-cross-origin**<br>
    Em uma requisição de mesma origem (HTTP→HTTP, HTTPS→HTTPS), envia origem, caminho e query string. Para requisições cross-origin e para destinos menos seguros (HTTPS→HTTP), envia apenas a origem.
* **same-origin**<br>
    Envia origem, caminho e query string para requisições de mesma origem. Não envia o cabeçalho para requisições cross-origin.
* **strict-origin**<br>
    Envia apenas a origem quando o nível de segurança do protocolo permanece o mesmo (HTTPS→HTTPS). Não envia o cabeçalho para destinos menos seguros (HTTPS→HTTP).
* **strict-origin-when-cross-origin (default)**<br>
    Envia origem, caminho e query string para requisições de mesma origem. Para requisições cross-origin, envia apenas a origem se o nível de segurança do protocolo for o mesmo (HTTPS→HTTPS). Não envia para destinos menos seguros (HTTPS→HTTP).
* **unsafe-url**<br>
    Envia origem, caminho e query string em qualquer requisição, independente da segurança.
    **Aviso:** Esse cabeçalho pode vazar informações privadas de URLs HTTPS para origens inseguras.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Dica

Comece configurando para ‘no-referrer’ para uma política de ‘compartilhamento zero’ ou ‘origin-when-cross-origin’, que permite analisar o tráfego em URLs do seu site e apenas o domínio de referência será enviado ao site externo.
</div>

### Política de Abertura entre Origens (Cross-Origin-Opener-Policy)

A terceira opção da primeira aba é a Política de Abertura entre Origens, um recurso de segurança do navegador que permite desconectar diferentes **‘Grupos de Contexto de Navegação’**.

![Joomla http headers 10](../../../en/images/security/http-headers-plugins-headers-cross-origin-opener-policy.png)

Um exemplo comum é o uso de pop-ups, onde o contexto original é desconectado de um novo contexto que é exibido no pop-up.

![Joomla http headers 10](../../../en/images/security/http-headers-plugins-headers-cross-origin-opener-popup.png)

> Essa opção de cabeçalho HTTP é complexa. Veja os links abaixo para entender melhor por que ela deve ser configurada.

A Política de Abertura entre Origens ajuda a fechar uma lacuna histórica na forma como os navegadores compartilham dados entre contextos, especialmente ao usar pop-ups.

Definir o **COOP** ajudará a mitigar ameaças de segurança, como a **‘Spectre’**. 

**COOP** isola dados do documento HTML original do HTML exibido em um pop-up. Isso evita ataques entre origens ou **XS-Leaks**.

Esse processo é semelhante ao familiar `rel="noopener"` que usamos em links regulares. Mas, ao contrário do `rel="noopener"`, que é ativo apenas em links externos, documentos que têm a política cross-origin-opener-policy configurada nos cabeçalhos HTTP pelo plugin do Joomla restringem dados em ambas as direções. Assim, o documento HTML com uma política COOP ativa não terá referência a ele no Cabeçalho HTTP, e a propriedade de Cabeçalho HTTP `window.opener` da nova janela será definida como `null`.

Ao definir essa opção no plugin de Cabeçalhos HTTP do Joomla, você tem 3 opções disponíveis.

* **unsafe-none**<br>
    Esse é o valor padrão. Permite que seu documento seja adicionado ao grupo de contexto de navegação de seu originador, a menos que o originador tenha uma política cross-origin-opener-policy de `same-origin` ou `same-origin-allow-popups`.
* **same-origin-allow-popups**<br>
    Essa opção mantém referências a janelas ou abas recém-abertas que não configuram uma política cross-origin-opener-policy ou que optam por sair do isolamento definindo uma política `cross-origin-opener-policy` de `unsafe-none`.
* **same-origin**<br>
    Isola o grupo de contexto de navegação apenas para documentos de mesma origem. Documentos de origem cruzada não são carregados no mesmo grupo de contexto de navegação.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Resumo

Um bom ponto de partida para o seu site é deixar essa opção configurada para `same-origin`, que é a configuração padrão. Isso permitirá que o conteúdo do seu próprio site/domínio seja carregado com sucesso em pop-ups, mas restringirá o carregamento de itens originados de uma fonte externa.

Conforme mencionado no início desta seção, alguns recursos avançados dependem do isolamento de origem cruzada. Recursos como objetos `SharedArrayBuffer` ou métodos `Performance.now()`, necessários para temporizadores sem limite por determinados service workers, estão disponíveis apenas se o documento tiver um Cabeçalho HTTP `cross-origin-opener-policy` com o valor `same-origin`.
</div>

### Forçar Cabeçalhos HTTP

A última opção da primeira aba é **Forçar Cabeçalhos HTTP**, que não deve ser confundida com ‘Forçar HTTPS’ nas configurações gerais do Joomla.

![Joomla http headers 11](../../../en/images/security/http-headers-plugins-force-http-headers.png)

Esta seção do plugin de Cabeçalhos HTTP do Joomla permite que você adicione, se desejar, uma seleção de cabeçalhos ‘outros’ que não estão detalhados nas abas do plugin, além de forçar a inclusão de alguns dos que estão incluídos.

No menu suspenso, você tem atualmente 10 opções. Vale a pena notar que algumas dessas **podem ser removidas com o tempo**, pois as políticas de cabeçalhos às quais se referem estão sujeitas a alterações ou reinterpretações.

Os cabeçalhos HTTP que você pode definir diretamente aqui direcionam para os seguintes:

Você pode obter mais informações sobre cada recurso no site de desenvolvedores da Mozilla.

#### Content-Security-Policy (lista)

O cabeçalho de resposta Content-Security-Policy permite que sites controlem os recursos que o usuário pode carregar para cada página da web. As políticas especificam principalmente origens de servidores e pontos de extremidade de script, ajudando a proteger contra ataques de script entre sites (XSS).
Mozilla: Content-Security-Policy

#### Content-Security-Policy-Report-Only

O cabeçalho de resposta HTTP Content-Security-Policy-Report-Only permite que os desenvolvedores da web experimentem políticas monitorando (mas não aplicando) seus efeitos.
Mozilla: Content-Security-Policy-Report-Only

#### Cross-Origin-Opener-Policy (COOP)

O cabeçalho de resposta HTTP Cross-Origin-Opener-Policy (COOP) permite garantir que um documento de nível superior não compartilhe um grupo de contexto de navegação com documentos de origem cruzada.
Mozilla: Cross-Origin-Opener-Policy

O COOP isola o processo do documento, evitando que invasores acessem o objeto global se ele fosse aberto em um pop-up, prevenindo uma série de ataques de origem cruzada conhecidos como **XS-Leaks**.

#### Expect-CT (A Ser Descontinuado)

O cabeçalho Expect-CT permite que sites optem por relatórios e/ou aplicação dos requisitos de Transparência de Certificado, para evitar que o uso de certificados emitidos incorretamente para aquele site passe despercebido.
Mozilla: Expect-CT (A Ser Descontinuado)

#### Feature-Policy (Agora Obsoleto)

O cabeçalho HTTP Feature-Policy fornece um mecanismo para permitir e negar o uso de recursos do navegador em seu próprio quadro e em conteúdo dentro de quaisquer elementos &lt;iframe&gt; no documento.
Mozilla: Feature-Policy

#### Permissions-Policy

Este é o substituto para o Feature-Policy acima.
Mozilla: Permissions-Policy (Substitui o Feature-Policy Acima)

#### Referrer-Policy (na lista)

O cabeçalho HTTP Referrer-Policy controla a quantidade de informações de referência (enviadas com o cabeçalho Referer) que deve ser incluída com as solicitações.
Mozilla: Referrer-Policy

#### Report-To

Parte da Content-Security-Policy. O cabeçalho de resposta HTTP Content-Security-Policy Report-To instrui o agente do usuário a armazenar pontos de relatório para uma origem.
Mozilla: Report-To

A diretiva `report-to` foi criada para substituir a diretiva `report-uri`, que é obsoleta, mas `report-to` ainda não é suportada na maioria dos navegadores.

#### Strict-Transport-Security

O cabeçalho de resposta HTTP Strict-Transport-Security (frequentemente abreviado como HSTS) informa aos navegadores que o site deve ser acessado apenas usando HTTPS, e que qualquer tentativa futura de acesso usando HTTP deve ser automaticamente convertida para HTTPS.
Mozilla: Strict-Transport-Security

Isso é mais seguro do que configurar apenas um redirecionamento HTTP para HTTPS (301) em seu servidor, onde a conexão HTTP inicial ainda está vulnerável a um ataque man-in-the-middle.

#### X-Frame-Options (na lista)

O cabeçalho de resposta HTTP X-Frame-Options indica se um navegador deve permitir que uma página seja renderizada em um &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; ou &lt;object&gt;. Os sites podem usar isso para evitar ataques de click-jacking, garantindo que seu conteúdo não seja incorporado a outros sites.
Mozilla: X-Frame-Options

A segurança adicional é fornecida apenas se o usuário que acessa o documento estiver usando um navegador que suporte X-Frame-Options.

O cabeçalho X-Frame-Options possui itens filhos chamados `frame-ancestors`, que substituem o cabeçalho Frame-Options. Se um recurso tiver ambas as políticas, a política `frame-ancestors` será aplicada e a política X-Frame-Options será ignorada.

Usando o campo de Valor do Cabeçalho HTTP, você pode definir os valores que deseja que sejam seguidos e atribuí-los ao seu site, ao site administrativo ou a ambos.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Resumo

Vale mencionar que o suporte dos navegadores aos cabeçalhos HTTP varia, então é uma boa ideia verificar o suporte dos cabeçalhos antes de implementá-los para seu público-alvo.

Se você definir uma série de Cabeçalhos HTTP para seu site e o navegador do usuário não suportar essa opção de Cabeçalho, o navegador a ignorará.
</div>

## Configurações do Plugin de Cabeçalhos HTTP - ABA 2

### Segurança Estrita de Transporte (HSTS)

**A aba de Política de Segurança Estrita de Transporte está desativada por padrão.**

![Joomla http headers 12](../../../en/images/security/http-headers-plugins-headers-strict-transport-security.png)

Eu adoro pesquisar. Porque às vezes você se depara com um verdadeiro momento de "OMG!". Este é um desses momentos.

A Wikipédia afirma:

> A Netscape Communications criou o HTTPS em 1994 para seu navegador web Netscape Navigator. Originalmente, o HTTPS era usado com o protocolo SSL. À medida que o SSL evoluiu para o protocolo de Segurança da Camada de Transporte (TLS), o HTTPS foi formalmente especificado pelo RFC 2818 em maio de 2000. O Google anunciou em fevereiro de 2018 que seu navegador Chrome marcaria sites HTTP como "Não Seguro" após julho de 2018. Esta ação foi para incentivar os proprietários de sites a implementarem HTTPS, como um esforço para tornar a World Wide Web mais segura. ......

Quem diria que a Netscape inventou os protocolos HTTPS há tanto tempo? O que é ainda mais surpreendente é quanto tempo levou para implementá-lo na internet que conhecemos e amamos hoje.

Há anos, eles nos instigaram, intimidaram e finalmente nos ameaçaram para implementar o HTTPS em todos os nossos sites. A maioria de nós capitulou e a rede mundial de computadores agora está finalmente segura. Ou está?

Existem, no entanto, alguns resistentes, íntimos ou sites esquecidos que ainda usam apenas http para entregar seu conteúdo, embora com um aviso do Google/Firefox etc. de “Este site é inseguro”.

Uma rápida busca no Google revelou várias listas desatualizadas desses sites ‘culpados apenas de HTTP’. Embora, desde a publicação dessas listas, muitos sites tenham atualizado para HTTPS. No entanto, houve algumas exclusões óbvias de organizações que você pensaria que deveriam saber melhor.

Por exemplo:

* NGINX (http://nginx.org/)
* GNU (http://www.gnu.org/)
* A Universidade de Washington (http://www.washington.edu/)

De acordo com o w3techs.com, cerca de 20% de todos os sites ainda estão rodando somente em HTTP.

**Então, por que isso é um problema?**

Isso é um problema porque qualquer dado enviado e recebido pelo navegador do usuário está em risco de ser interceptado. Sabemos disso como um **ataque de homem no meio**. Agora, isso pode não parecer uma consideração importante se o seu site é apenas sobre fotos de gatinhos fofos.

![snapshot of cute kittens](../../../en/images/security/http-headers-plugins-headers-kittens.jpg)

Mas, mesmo sites simples podem se tornar vítimas de hackers e atacantes que implementarão **click-jacking** e outros ataques de origem cruzada que prejudicarão seus usuários.

Um site que não troca dados do usuário ou informações de login **deve ainda assim usar HTTPS**.

**Ok, vamos voltar ao tema.**

Como você já deve saber, o objetivo do HTTPS é introduzir uma conexão segura entre o navegador do usuário e seu servidor. Uma conexão onde qualquer troca de dados acontece em um ambiente seguro que não pode ser interceptado e copiado por um terceiro. Um homem no meio.

![man in the middle attack](../../../en/images/security/http-headers-plugins-headers-man-in-middle.png)

Mas, você sabia que, a menos que seu **Certificado SSL HTTPS** use **TLS**, sua conexão ‘segura’ não é tão segura quanto você esperaria? Conexões HTTPS sem TLS continuam **vulneráveis a ataques de homem no meio**.

Embora seja um post de blog antigo, este artigo explica bem como um ataque de homem no meio funciona.

Os navegadores adotaram amplamente o TLS.

E o TLS 1.3 não é diretamente compatível com as versões anteriores, a menos que esteja sendo executado no modo de compatibilidade. O que poderia representar um problema para alguns.

![tls certicate information](../../../en/images/security/http-headers-plugins-headers-tls.png)

Usar o Plugin de Cabeçalho HTTP do Joomla para lidar com Segurança Estrita de Transporte (HSTS) ajuda a mitigar ataques do tipo homem no meio ao forçar o uso de TLS no navegador web de seus visitantes. O TLS garante que toda a comunicação na web ocorra no lado do cliente usando uma camada de transporte segura.

**Você está usando um redirecionamento 301 para servir a versão HTTP não segura do seu site para a versão HTTPS segura?**

A maioria das pessoas usa. Os redirecionamentos 301 são instruções que a maioria dos proprietários de sites configura em seu arquivo htaccess. Eles informam ao Google que a versão do site que deve ser usada é a HTTPS (segura). O problema com isso é que **o 301 é apenas um redirecionamento de URL**, então seu site ainda faz algum elemento da conexão inicial através do HTTP.

Diferente das conexões entre um usuário e um servidor de site que usam HSTS, onde o servidor interage automaticamente com ele usando apenas HTTPS.

O HSTS tem uma fraqueza, no entanto, pois a primeira conexão inicial entre o navegador do usuário e o servidor do site ainda acontece através do HTTP. Mas todas as conexões subsequentes são automaticamente conectadas via HTTPS até que a data de expiração do Cabeçalho HTTP seja atingida e este cabeçalho seja redefinido.

Isso é diferente de um redirecionamento 301 padrão onde cada carregamento de página inclui uma solicitação http inicial para iniciar a conexão https.

Há uma solução para essa fraqueza nas configurações do HSTS de Cabeçalhos HTTP, ativar ‘Preload’.

O que adicionará a tag ‘Preload’ ao cabeçalho de resposta.

Nas configurações, há também uma lista de preload de link**. Esta é uma lista que está codificada em muitos navegadores modernos. A lista informa o navegador que a conexão com o example.com deve ser feita apenas via HTTPS. Assim, eliminando a necessidade de fazer a conexão inicial via HTTP.

![hsts preload](../../../en/images/security/http-headers-plugins-headers-enter-domain.png)

Uma vez que o HSTS está configurado no plugin de cabeçalho HTTP do Joomla, todas as tags necessárias são adicionadas ao cabeçalho de resposta HTTP. Isso informa a qualquer navegador de usuário que está tentando se conectar ao seu servidor que todas as conexões **devem ser feitas com HTTPS**, seja especificado em seu HTML ou não.

Em resumo, usar o plugin de cabeçalhos HTTP do Joomla para integrar o HSTS em vez de depender de redirecionamentos 301 para servir seu conteúdo via HTTPS é uma importante melhoria de segurança. Uma melhoria que ajuda a impedir **ataques de homem no meio** e proporciona ao seu usuário um ambiente seguro.

O HSTS cobre todo o domínio, diferente de um redirecionamento 301 que cobre apenas um caminho de URI específico.

O HSTS usa um cache de navegador separado que é geralmente segregado, então não pode ser facilmente ou acidentalmente limpo.

O HSTS pode ser pré-carregado em um navegador. Isso garante que um usuário se conecte ao seu servidor apenas com HTTPS, independentemente de ele já ter visitado o site antes ou não.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem;">
Resumo:

Ativar: HSTS

Definir max-age: O padrão é de 1 ano (31.536.000 segundos), mas alguns recomendam definir isso para 2 anos (63.072.000 segundos).

Ativar: Subdomínios - Se você tiver subdomínios, certifique-se de ter um certificado SSL válido para cobri-los individualmente ou como um coringa do seu domínio principal.

Ativar: Preload

Por fim, envie seu domínio para a lista de preload do HSTS.
</div>

## Configurações do Plugin de Cabeçalhos HTTP - ABA 3

### Política de Segurança de Conteúdo (Aba 3)

**A aba de Política de Segurança de Conteúdo está desativada por padrão.**

Quando você ativa a Política de Segurança de Conteúdo do Joomla por meio do plugin de Cabeçalhos HTTP, você informa ao navegador do visitante exatamente quais recursos devem ser carregados do servidor do seu site. Essa é uma maneira excelente de garantir que apenas o conteúdo desejado seja entregue.

![aba de política de segurança de conteúdo](../../../en/images/security/http-headers-plugins-headers-csp.png)

Ter uma Política de Segurança de Conteúdo eficaz é uma forma eficaz de impedir ataques de **Cross-Site Scripting (XSS)** e **Click Jacking** que possam se originar no seu site.

Cross-Site Scripting, ou ataque **XSS**, é um ataque em que um script malicioso é "injetado" em um site confiável e desavisado. Os invasores exploram um ponto fraco, geralmente onde o usuário pode inserir dados.

Componentes desatualizados que permitem entrada de usuários, como formulários de comentário sem validação, podem ter vulnerabilidades que são exploradas em ataques XSS. Por isso, é sempre recomendável manter os componentes do Joomla atualizados e minimizar essas oportunidades.

**Usando um formulário de comentários infectado como exemplo:**

Seu site usa um formulário de comentários ao final de um artigo para promover a discussão dos usuários. Excelente.

Seu plugin de comentários de um site questionável funciona bem e seus usuários adoram. No entanto, você não o atualiza há 5 anos e os desenvolvedores já o abandonaram há muito tempo.

Agora, 5 anos depois, um invasor percebe que, devido a uma vulnerabilidade no código do componente de comentários, ele pode esconder um código malicioso em um comentário aparentemente inofensivo.

O que esse código faz pode variar, mas, toda vez que a página do artigo carrega, o código também é carregado e executado. Como faz parte do HTML, o navegador não sabe que não deveria estar lá.

Então, o código malicioso é executado. Ele pode verificar seus cookies, roubar dados sensíveis do navegador ou carregar anúncios de sites indesejados. Talvez até mesmo substitua o HTML para roubar dados do usuário.

**Na verdade, um script pode ser executado para realizar quase qualquer coisa.**

Uma boa Política de Segurança de Conteúdo ajuda a impedir esse tipo de ataque, mesmo se o plugin de comentários comprometido for o alvo.

Isso é possível porque o plugin de Cabeçalhos HTTP do Joomla entrega a CSP como um cabeçalho de resposta HTTP, **especificando ao navegador o que carregar**. Nas configurações da aba CSP do plugin, você pode definir **28 Diretivas de Política** para garantir que seu site use apenas fontes aprovadas para seus arquivos e conteúdo.

O exemplo de ataque acima envolvia o carregamento de um arquivo JavaScript de outra fonte para alterar o HTML renderizado na tela. Isso poderia ser evitado adicionando a diretiva script-src 'self' à CSP do Joomla no plugin.

![diretiva de política self](../../../en/images/security/http-headers-plugins-headers-policy-directive.png)

Neste exemplo, o navegador só carregará arquivos JavaScript do domínio do seu site. Todos os outros serão rejeitados, incluindo o do invasor.

Enquanto isso ajuda a proteger o site, também pode bloquear arquivos JavaScript legítimos que você deseja carregar. Esses arquivos externos podem ser adicionados como fontes permitidas na mesma diretiva. Por exemplo, se você usa o bootstrap de um CDN, adicione:
```
script-src 'self' https://cdn.jsdelivr.net
```
Caso tenha dificuldades ao carregar o bootstrap do CDN, tente adicionar a URL completa do arquivo necessário: `script-src 'self' https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js`.

![diretiva de política self](../../../en/images/security/http-headers-plugins-headers-policy-directive-self.png)

Adicionar essas fontes externas seria mais fácil em um site novo. Mas, se inspecionar o HTML renderizado com as Ferramentas de Desenvolvedor, você deve encontrar todos os arquivos externos e incluí-los na CSP.

Ao adicionar diretivas à Política de Segurança de Conteúdo no Plugin de Cabeçalhos HTTP, existem alguns **valores principais** que você pode usar para definir o que deve ser explicitamente carregado pelo navegador. Estes são os básicos para configurar a primeira Política de Segurança de Conteúdo.

Outras opções estão disponíveis para algumas diretivas avançadas. A lista completa e exemplos podem ser encontrados no site Guia Rápido de Referência da CSP.

* **'none'** bloqueia o uso desse tipo de recurso.
* **'self'** corresponde à origem atual (mas não subdomínios).
* **'unsafe-inline'** permite o uso de JS e CSS inline.
* **'unsafe-eval'** permite o uso de mecanismos como eval().

Agora, vejamos algumas dessas diretivas. Aqui está uma lista das diretivas disponíveis no plugin de Cabeçalhos HTTP do Joomla, com uma breve descrição, cortesia da Política de Segurança de Conteúdo.

<dl>
<dt>default-src</dt>
<dd>A diretiva default-src define a política padrão para busca de recursos como JavaScript, Imagens, CSS, Fontes, solicitações AJAX, Frames, Mídia HTML5.<br>
EXEMPLO DE POLÍTICA DEFAULT-SRC<br>
default-src 'self' https://cdn.example.com
</dd>
<dt>script-src</dt>
<dd>Define fontes válidas de JavaScript.<br>
EXEMPLO DE POLÍTICA SCRIPT-SRC<br>
script-src 'self' https://js.example.com
</dd>
<dt>style-src</dt>
<dd>Define fontes válidas para folhas de estilo ou CSS.<br>
EXEMPLO DE POLÍTICA STYLE-SRC<br>
style-src 'self' css.example.com
</dd>
<dt>img-src</dt>
<dd>Define fontes válidas para imagens.<br>
EXEMPLO DE POLÍTICA IMG-SRC<br>
img-src 'self' https://img.example.com https://example.com
</dd>
<dt>connect-src</dt>
<dd>Aplica-se a XMLHttpRequest (AJAX), WebSocket, fetch(), &lt;a ping&gt; ou EventSource. Se não permitido, o navegador emula o código de status HTTP 400.<br>
EXEMPLO DE POLÍTICA CONNECT-SRC<br>
connect-src 'self'
</dd>
<dt>font-src</dt>
<dd>Define fontes válidas para recursos de fontes (carregadas via @font-face).<br>
EXEMPLO DE POLÍTICA FONT-SRC<br>
font-src https://font.example.com https://example.com
</dd>
<dt>object-src</dt>
<dd>Define fontes válidas para plugins, como &lt;object&gt;, &lt;embed&gt; ou &lt;applet&gt;.<br>
EXEMPLO DE POLÍTICA OBJECT-SRC<br>
object-src 'self'
</dd>
<dt>media-src</dt>
<dd>Define fontes válidas para áudio e vídeo, por exemplo, elementos HTML5 &lt;audio&gt;, &lt;video&gt;.<br>
EXEMPLO DE POLÍTICA MEDIA-SRC<br>
media-src https://media.example.com
</dd>
<dt>frame-src</dt>
<dd>Define fontes válidas para carregamento de frames. No CSP Nível 2, frame-src foi depreciado em favor de child-src. No CSP Nível 3, frame-src foi restaurado e continua a deferir para child-src se não presente.<br>
EXEMPLO DE POLÍTICA FRAME-SRC<br>
frame-src 'self'
</dd>
<dt>sandbox</dt>
<dd>Ativa uma sandbox para o recurso solicitado, semelhante ao atributo de sandbox de iframe. A sandbox aplica uma política de mesma origem, previne pop-ups, plugins e bloqueia execução de scripts. Mantenha o valor vazio para restrições ou adicione valores: allow-forms, allow-scripts, allow-pop-ups, etc.<br>
EXEMPLO DE POLÍTICA SANDBOX<br>
sandbox allow-forms allow-scripts
</dd>
<dt>report-uri</dt>
<dd>Instrui o navegador a enviar relatórios de falhas para um URI. No CSP Nível 3, foi depreciada em favor da diretiva report-to.<br>
EXEMPLO DE POLÍTICA REPORT-URI<br>
report-uri /some-report-uri
</dd>
<dt>child-src</dt>
<dd>Define fontes válidas para web workers e contextos de navegação aninhados.<br>
EXEMPLO DE POLÍTICA CHILD-SRC<br>
child-src 'self'
</dd>
<dt>form-action</dt>
<dd>Define fontes válidas que podem ser usadas como ação de um HTML &lt;form&gt;.<br>
EXEMPLO DE POLÍTICA FORM-ACTION<br>
form-action 'self'
</dd>
<dt>frame-ancestors</dt>
<dd>Define fontes válidas para incorporar o recurso em &lt;frame&gt; &lt;iframe&gt; &lt;object&gt; &lt;embed&gt; &lt;applet&gt;. Definir como 'none' é equivalente a X-Frame-Options: DENY.<br>
EXEMPLO DE POLÍTICA FRAME-ANCESTORS<br>
frame-ancestors 'none'
</dd>
<dt>plugin-types</dt>
<dd>Define tipos MIME válidos para plugins invocados via &lt;object

&gt; e &lt;embed&gt;. Depreciado no CSP Nível 3.<br>
EXEMPLO DE POLÍTICA PLUGIN-TYPES<br>
plugin-types application/pdf
</dd>
</dl>

Como você pode ver, muitas diretivas permitem que você escolha o que deseja carregar no site.

O plugin de Cabeçalhos HTTP do Joomla também oferece a opção de **definir alguns parâmetros globais na aba de Política de Segurança de Conteúdo (CSP)**.

![Joomla http headers 14](../../../en/images/security/http-headers-plugins-headers-csp-global.png)

Você pode escolher aplicar a CSP ao seu site, ao site do administrador ou a ambos com a configuração de cliente.

A opção ‘Somente para Relatório’ permite que você teste suas diretivas e as verifique quanto a erros nas Ferramentas do Desenvolvedor antes de colocar em produção. É sempre interessante rastrear o motivo dos erros de CSP no console do Google!

Em seguida, vem a configuração de ‘Nonce’. Nonce, que significa ‘número usado uma vez’, é um sistema que aplica uma string gerada aleatoriamente a uma tag &lt;script&gt; ou &lt;style&gt; inline que é incluída no HTML por meio da API do Joomla. Essas instâncias são geralmente implementadas por desenvolvedores de componentes/módulos/plugins de terceiros do Joomla quando você adiciona funcionalidades extras ao seu site.

Na imagem abaixo, você pode ver a tag &lt;style&gt; com um atributo nonce rel adicionado aos &lt;styles&gt; CSS incluídos no documento HTML pelo componente Akeeba Backup.

![Joomla http headers 16](../../../en/images/security/http-headers-plugins-headers-akeeba-style.png)

Interessantemente, o código JavaScript e CSS do Joomla core que é adicionado ao documento HTML atualmente não inclui uma tag ‘nonce’. Isso ocorre porque **eles fazem parte do ‘core’** em vez de serem adicionados por meio da API do Joomla.

Se você ativar a alternância ‘Nonce’ nas configurações de CSP, esses scripts e estilos inline serão renderizados pelo navegador como ‘seguros’. Você também terá que definir a tag {nonce} do Joomla na sua diretiva de política script-src para script-src 'self' {nonce}. Como alternativa para navegadores mais antigos que não suportam 'nonces', você também pode adicionar {script-hashes} após o marcador {nonce}, como script-src 'self' {nonce} {script-hashes} (atenção ao espaçamento). Mas não se esqueça de ativar **Hashes de Script** primeiro.

![Configurações de nonce do Joomla](../../../en/images/security/http-headers-plugins-headers-nonce-settings.png)

O Joomla gera aleatoriamente a string de texto ‘nonce’ e a adiciona às tags &lt;style&gt; e &lt;script&gt;. Quando você ativa a opção ‘nonce’ nas configurações do plugin, a string de texto é passada para o Cabeçalho HTTP. O navegador então interpreta o Cabeçalho HTTP e processa as tags &lt;script&gt; ou &lt;style&gt; correspondentes. Ao mesmo tempo, ele remove a string de texto Nonce do HTML renderizado no navegador.

![Estilo de nonce do Joomla](../../../en/images/security/http-headers-plugins-headers-nonce-style.png)

Isso, por sua vez, impede que o Sr. Hacker consiga sequestrar a string de texto nonce e adicioná-la ao seu próprio código injetado. Mesmo que o Sr. Hacker consiga injetar seu JavaScript malicioso no seu HTML, o navegador o bloqueará.

### Hashes de Script

Todos sabemos que não deveríamos incluir JavaScript inline em nosso HTML; é melhor escrevê-lo em um arquivo `meu-javascript.js` e adicioná-lo ao &lt;head&gt; ou antes da tag &lt;/body&gt;. Mas todos fazemos isso de vez em quando.

O problema é que, se você fizer isso e adicionar a diretiva CSP ‘script-src 'self'’, todo JavaScript inline será bloqueado por padrão. A intenção é justamente essa, para evitar que o JavaScript injetado pelo Sr. Hacker consiga ser executado no seu site.

Existe uma forma de contornar isso com a diretiva script-src 'unsafe-inline', que permite que o JavaScript inline do Sr. Hacker seja executado, assim como o seu código confiável. Esta não é a melhor opção, por razões óbvias.

**É aí que os Hashes de Script entram em cena!**

O plugin de Cabeçalhos HTTP do Joomla coleta automaticamente todos os &lt;styles&gt; e &lt;scripts&gt; **passados pela API do Joomla** para o site. Ele então gera os respectivos hashes e os passa pelo Cabeçalho HTTP. O navegador então gera os hashes no próprio site e confirma que os hashes coincidem. Se sim, os scripts são executados; caso contrário, são bloqueados.

Para ativar esse recurso do plugin, alterne o botão para **'Habilitado'**. Em seguida, na sua diretiva de política script-src, adicione o valor 'self' {script-hashes}. Se você estiver usando o recurso 'nonce' junto com os 'hashes de script', defina o valor da diretiva conforme o exemplo de nonce acima.

![Hashes de script do Joomla](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes.png)

**Agora, isso é inteligente.**

Mas, ainda melhor, é que podemos usar a mesma ideia para processar manualmente hashes de script e adicioná-los à nossa diretiva script-src 'self'. Isso exigirá um pouco de trabalho para configurar e manter, mas pode ser muito útil se você adicionou algum JavaScript a um artigo ou módulo personalizado.

Existem maneiras mais detalhadas de fazer isso usando um gerador de hash sha256, sha384 ou sha512. Mas, como a maioria das pessoas só adiciona pequenos trechos de JavaScript ao artigo ou módulo personalizado, vamos deixar as Ferramentas do Desenvolvedor do Google fazerem o trabalho para nós.

O processo é simples. A única diferença é como geramos o hash.

Suponha que você ativou o plugin de Cabeçalhos HTTP do Joomla, que o CSP está ativo e você tem a diretiva script-src 'self' configurada e salva.

Passo 1 - Adicione seu JavaScript inline ao artigo ou módulo personalizado e salve. Não se esqueça de ajustar as configurações do editor para evitar que ele remova seu código ao salvar.

Passo 2 - Navegue até a página da web com o script. Abra as Ferramentas do Desenvolvedor e, na aba de console, você verá um erro semelhante a este:

Refused to execute inline script because it violates the following Content Security Policy directive: "script-src 'self'". Either the 'unsafe-inline' keyword, a hash ('sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='), or a nonce ('nonce-...') is required to enable inline execution.

![Ferramentas de Desenvolvedor Joomla hashes de script](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes-tools-error.png)

Passo 3 - Agora, basta copiar/colar o hash da mensagem de erro na sua diretiva de JavaScript no plugin e salvar novamente:

script-src 'self' 'sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='

![Diretiva de hashes de script Joomla](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash.png)

Em seguida, recarregue a página e verifique novamente nas Ferramentas do Desenvolvedor do Google. O erro agora desaparecerá e o navegador carregará seu script na página.

**Observação:** Ainda há um erro mostrando em meu exemplo, pois o JavaScript adicionado ao meu artigo não está completo. Mas, ele mostra que o código inline está, pelo menos, tentando funcionar.

Adicionar hashes ao seu código inline é uma boa forma de incluí-los na lista de permissões do cabeçalho HTTP para que ainda sejam executados, enquanto qualquer código inline que não tenha sido explicitamente hasheado e adicionado ao CSP ainda será bloqueado. Isso impede que o Sr. Hacker tente comprometer seu site.

![Erro de Ferramentas do Desenvolvedor Joomla](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash-tools-error.png)

**Observação:**

Se você alterar seu JavaScript, precisará recalcular o hash e mudar o valor na diretiva de CSP.

Se tiver problemas para fazer com que seus hashes funcionem, há 3 problemas comuns e você pode encontrar soluções na página **Usando um hash com CSP**.

**Strict Dynamic**

Se você ativar a opção Strict Dynamic em seu CSP, isso tomará a autoridade explícita que você deu a um script por meio de um Hash ou Nonce e aplicará a qualquer outro script diretamente vinculado ou chamado a partir dele. Esta ação também anula diretivas padrão, como 'self' ou 'unsafe-inline', aplicadas em suas diretivas CSP gerais para esses scripts secundários, ignorando-as.

**Hashes de Estilo**

O Hash de Estilo do CSP funciona exatamente como os hashes de JavaScript descritos acima, mas use-o se adicionar blocos CSS &lt;style&gt; no corpo do seu HTML. Assim como usar **Hashes de Script** ativa o recurso de plugin e define uma Diretiva de Política style-src para referenciá-lo com o valor 'self' {style-hashes}.

![Hash de estilo do Joomla](../../../en/images/security/http-headers-plugins-headers-csp-style-hash.png)

**Observação:**

Se você alterar seu CSS inline, em vez do CSS que é criado pela API do Joomla, precisará recalcular seu hash e alterar o valor na diretiva de CSP.

**Frame Ancestors ‘self’**

Esta opção

 no plugin permite que uma página seja enquadrada, por exemplo, dentro de um iframe, mas somente do mesmo site.

Se você quiser permitir explicitamente que outro site enquadre seu conteúdo, poderá configurar uma diretiva específica ‘frame-src’.

![Frame Ancestors Joomla](../../../en/images/security/http-headers-plugins-headers-csp-style-hash-frame-src.png)

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Resumo

Às vezes, uma boa CSP é mais fácil de configurar em um site novo conforme você configura os recursos externos necessários.

É importante usar o URL base completo e correto para o domínio permitido na Diretiva CSP. Por exemplo: https://www.meusite.com.br ou https://www.outrosite.com.

Também é possível direcionar subdomínios com a mesma CSP usando curingas. Por exemplo: https://*.exemplo.org.

Nem todos os navegadores suportam todas as diretivas.

CSP suporta Hashes sha256, sha384 e sha512.
</div>

## Nota Final / Conclusão:

Ao escrever este artigo, percebi que apenas arranhei a superfície deste enorme tópico.

Adoro descobrir assuntos que anteriormente ignorei ou desconhecia. Você é assim também?

A conclusão a que cheguei ao pesquisar sobre o tópico dos Cabeçalhos HTTP, e em particular, ao usar o novo plugin J4 do Joomla para defini-los, é que todos precisamos dominar este assunto. Há muitas pessoas (hackers) por aí apenas esperando por uma oportunidade para tirar proveito de sites com segurança fraca. Portanto, não ajude seus usuários a se tornarem vítimas.

Divirta-se explorando o plugin de cabeçalhos HTTP do Joomla e aprenda como ele pode ajudar a proteger seu site.

Antes de começar, recomendo que faça mais pesquisas sobre este tópico interessante. Há links abaixo para iniciar sua própria pesquisa. Isso lhe dará uma compreensão muito melhor de como a internet funciona e de como seu site interage com ela.

### Para Referência

Se você precisar redefinir o plugin, o plugin HTTP Headers foi instalado com as seguintes opções configuradas:

O plugin está ativado por padrão.

* As abas HSTS e CSP estão desativadas por padrão.
* As X-Frame-Options estão ativadas por padrão.
* A Referrer-Policy está inicialmente configurada para: strict-origin-when-cross-origin.
* A Cross-Origin-Opener-Policy está inicialmente configurada para same-origin.

Se você leu até aqui e pensou "Isso não é justo, e o J3?", "Por que não podemos ter as mesmas funcionalidades no Joomla 3?". Bem, a boa notícia é que você pode. Embora você precise baixar o plugin do [JED].

Depois de configurar seus cabeçalhos HTTP com o plugin do Joomla 4, você pode testar seus Cabeçalhos HTTP no site Security Headers.

Como você se saiu?

Esteja ciente de que a ativação do plugin HTTP Headers pode ter ações inesperadas na interface do usuário.

Finalmente, gostaria de agradecer a Tobias Zulauf & Ced Keiflin por suas contribuições em finalizar este artigo a tempo!

