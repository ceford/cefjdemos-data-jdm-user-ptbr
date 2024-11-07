<!-- Filename: WebAuthn_Passwordless_Login / Display title: Login WebAuthn -->

## Login sem Senha com WebAuthn

A Autenticação na Web, ou WebAuthn para abreviar, permite que um usuário faça login com segurança em um site sem usar uma senha — embora um nome de usuário ainda seja necessário. Ela utiliza criptografia forte de uma maneira que é extremamente resistente aos problemas mais comuns das senhas:
* alguém a adivinhou (ataque de força bruta)
* alguém a interceptou (ataque do homem no meio)
* alguém o enganou para divulgá-la (ataque de phishing)
* alguém a quebrou após obter uma cópia dos dados de seu banco de dados (ataques de injeção de SQL)
* alguém a roubou.

WebAuthn não é apenas muito seguro; também é muito fácil de usar! Você não precisa mais se lembrar de senhas longas ou usar um gerenciador de senhas. Tudo o que você precisa é de um *autenticador*, às vezes também chamado de *chave de acesso*.

Um autenticador pode ter muitas formas, físicas ou virtuais. Ele pode ser uma chave de hardware separada conectando-se ao seu dispositivo via USB, Bluetooth ou NFC. Pode ser o próprio dispositivo, desbloqueando seu autenticador integrado com um PIN, leitor de impressão digital, reconhecimento facial ou verificação biométrica semelhante.

Esse recurso já funciona em dispositivos Android e iOS/iPadOS e estamos trabalhando para habilitá-lo no Windows também. Pode até ser o seu telefone — atualmente isso é possível com telefones Android, mas esse recurso também está chegando aos dispositivos iOS / iPadOS.

WebAuthn só funciona em HTTPS e apenas quando seu site está usando um certificado válido e confiável para isso. Não se preocupe, você não precisa gastar dinheiro extra; serviços gratuitos como o Let's Encrypt são geralmente integrados aos painéis de controle de hospedagem na web e funcionam perfeitamente com o WebAuthn.

WebAuthn usa criptografia de chave pública, a mesma tecnologia comprovada que mantém seus sites seguros com HTTPS, suas informações bancárias seguras e assim por diante. A chave privada nunca sai do autenticador. Seu site apenas armazena uma chave pública. Mesmo que você sofra uma violação de dados, o atacante ficará apenas com uma chave pública praticamente inútil; levaria milhares a milhões de anos de CPU para quebrá-la, em oposição a poucos minutos ou horas necessários para quebrar o hash de uma senha fixa que você pode lembrar.

WebAuthn é o futuro da autenticação. Fácil, seguro e sem complicações. Tudo o que senhas fixas não são.

A imagem a seguir mostra um dispositivo de hardware inserido na porta USB de um computador portátil. Custou £15 em fevereiro de 2022.

![fotografia do dispositivo de hardware](../../../en/images/users/passwordless-login-hardware-device.jpg)

WebAuthn usa um plugin do sistema que está habilitado por padrão. Um botão de **Autenticação na Web** estará presente nas telas de login padrão do Joomla 4 e posteriores, como ilustrado na tela de login do Administrador:

![formulário de login seguro do administrador](../../../en/images/users/passwordless-login-login-form.jpg)

## Configuração do Usuário

O usuário deve primeiro se registrar com um Nome de Usuário e Senha. Depois de fazer o login, vá para o formulário de Perfil do Usuário. Para um Administrador:

- Selecione **Menu do Usuário → Editar Conta → Autenticação Web W3C
  (WebAuthn) Login** para abrir o formulário, inicialmente sem
  autenticadores registrados.
- Selecione **Adicionar Novo Autenticador**

A apresentação exata do próximo passo depende do seu navegador.
Normalmente, você verá um alerta, mensagem ou janela pedindo para selecionar
um tipo de autenticador ou, se você estiver usando um autenticador de hardware
conectado ao seu dispositivo, lembrando você de pressionar o botão no
autenticador de hardware. Por motivos de segurança e praticidade, há um
intervalo de tempo relativamente curto permitido para ativar o autenticador:
60 segundos.

![prompt seguro de login de administrador com hardware](../../../en/images/users/passwordless-login-hardware-propmpt.png)

Uma vez que você desbloquear seu autenticador — tocando em um botão, escaneando sua
impressão digital / rosto, inserindo um PIN ou uma combinação dos acima
dependendo do seu autenticador — a mensagem desaparece, o
autenticador é registrado e a tela aparece como segue:

![login seguro de administrador autenticador registrado](../../../en/images/users/passwordless-login-registered-authenticator.png)

É muito importante notar que você só pode registrar ou remover
autenticadores na sua própria conta de usuário. Por motivos de segurança, mesmo um
Super Usuário não pode registrar, editar ou adicionar
autenticadores em outras contas de usuário.

### Autenticadores

Você pode usar qualquer autenticador FIDO U2F ou FIDO2. FIDO U2F é um padrão mais antigo
que suporta uma seleção mais limitada e menos segura de
métodos criptográficos. FIDO2 é o padrão mais recente que suporta métodos
criptográficos muito mais seguros, incluindo Criptografia de Curva Elíptica,
um método criptográfico que é considerado resistente até mesmo à computação quântica
(se e quando isso se tornar uma realidade prática). Além disso, autenticadores FIDO2
podem ser configurados para ter proteções adicionais, como um
PIN ou um controle biométrico (por exemplo, escaneamento de impressão digital), o que
significa que mesmo se você perder a posse física do próprio autenticador, quem
encontrá-lo não poderá acessar seus sites.

Se você estiver procurando comprar um autenticador de hardware, pode procurar
"FIDO2" no seu marketplace favorito, como a Amazon. Há uma ampla
seleção para escolher.

Você também pode usar uma chave FIDO de software, como o Krypton, como seu
autenticador.

Muitos dispositivos têm autenticação compatível com FIDO2 integrada:

- Windows 10 e 11 têm Windows Hello com um PIN, leitor de impressão digital,
  câmera de reconhecimento facial ou uma combinação de chave de hardware e PIN.
  O suporte para Windows Hello está sendo adicionado ao plugin com uma meta de lançamento
  para o Joomla 4.2.0.
- macOS tem TouchID em todos os laptops com o chip T2 ou aqueles baseados em
  Apple Silicon usando o sensor TouchID integrado, bem como todos os desktops
  baseados em Apple Silicon usando o novo teclado Apple Aluminium com um
  leitor de impressão digital.
- iOS / iPadOS tem TouchID em todos os dispositivos com um leitor de impressão digital
  e FaceID em todos os dispositivos mais novos com uma câmera de projeção
  infravermelha FaceID.
- Alguns dispositivos Android possuem um leitor de impressão digital ou uma câmera
  de reconhecimento facial. Estes também podem funcionar como autenticadores FIDO2, no Android 9 ou
  posterior usando o Google Chrome.
- Outros dispositivos também podem estar disponíveis. Por exemplo, telefones Android usando
  ![caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### Navegadores compatíveis com WebAuthn

Navegadores baseados em Chromium e Firefox têm suportado WebAuthn desde o início de 2019.

Safari e todos os navegadores iOS/iPadOS (que são, na verdade, Safari com uma
interface diferente) suportam totalmente WebAuthn desde que iOS/iPadOS 13 foi lançado no final de 2019.

Praticamente falando, se o seu sistema operacional e navegador foram lançados
após meados de 2020, você não deve ter problemas. Apenas alguns navegadores muito incomuns ainda não oferecem suporte ao WebAuthn.

## Autenticação

Para fazer login, você deve inserir seu nome de usuário no campo Nome de Usuário do formulário de login. Você não precisa digitar sua senha, mas se o seu navegador a inserir para você, apenas deixe-a. A senha NÃO é enviada para o servidor quando o formulário é enviado via o botão de Autenticação Web.

Isso significa que você pode fazer login com seu Nome de Usuário e Senha ou Nome de Usuário e Autenticação Web.

## Como Desativar o Plugin

Se você não deseja permitir o WebAuthn, basta ir até a lista de plugins, encontrar Sistema - Login Sem Senha WebAuthn no grupo Sistema e desativá-lo. Não há parâmetros para configurar.

## Requisitos do Servidor

Para que o WebAuthn funcione, as seguintes condições prévias devem ser atendidas:

- HTTPS com um certificado válido e assinado. A maioria dos hosts permite que você use certificados gratuitos emitidos pelo Let's Encrypt. Estes funcionam perfeitamente com WebAuthn.
- A extensão OpenSSL para PHP deve estar instalada e habilitada.
- A extensão PHP GMP ou a extensão PHP BCmath deve estar instalada e habilitada (qualquer uma das duas serve).
- A biblioteca Sodium deve idealmente estar habilitada; ela permite o uso de Criptografia de Curva Elíptica em autenticadores FIDO2 compatíveis, que, como dissemos, é o método criptográfico mais seguro.

## Perguntas Frequentes e Solução de Problemas

### Eu não consigo ver o botão de login "Autenticação na Web"

Você não está acessando seu site por HTTPS. O WebAuthn está disponível apenas para sites HTTPS com um certificado válido. Esta é uma precaução de segurança embutida no padrão WebAuthn. Na verdade, o plugin verifica se o site é acessado através de HTTPS usando a classe Uri do Joomla. Em raros casos onde o servidor mente sobre o protocolo, você pode não ver o botão, mesmo que seu site (afirme ser) HTTPS. O mesmo acontece se você editou seu arquivo configuration.php e configurou o parâmetro opcional \$live_site com um prefixo de protocolo http:// em vez de https://.

Note também que módulos de login de terceiros e componentes que implementam seu próprio formulário de login podem ainda não exibir esses botões. Adicionamos nova infraestrutura para suportá-los, assim como tivemos que fazer no Joomla! 3.2 para suportar a Autenticação de Dois Fatores.

### Ainda preciso fornecer um nome de usuário. O WebAuthn não deveria eliminar o uso de nomes de usuário?

Na verdade, não. A especificação atual do WebAuthn não oferece gerenciamento de identidade. Navegadores exigem que enviemos uma lista de chaves públicas WebAuthn aceitáveis durante a fase de login. Isso significa que precisamos do seu nome de usuário para buscá-las.

Dito isso, o uso do WebAuthn finalmente deixa claro que nomes de usuário *não são para serem considerados segredos*. Eles são considerados informações públicas que podem ser transmitidas livremente para um adversário, assim como as chaves públicas armazenadas no banco de dados do site. O único segredo é armazenado no autenticador e nunca sai dele!

### Eu registrei um autenticador, mas ao tentar fazer login sou informado que não o fiz. Isso é um bug?

É um bug, mas não do próprio plugin WebAuthn.

Um ou mais plugins no seu site geram Notificações, Alertas ou Erros de PHP, corrompendo assim a resposta enviada de volta pelo seu servidor. Como resultado, o JavaScript na página não consegue analisar a resposta do servidor e não tem certeza se algum autenticador está registrado pelo usuário.

Vá para o backend do seu site, Sistema, Configuração Global e configure o Relatório de Erros para Nenhum. Na maioria dos casos de plugins básicos e de terceiros que estão se comportando mal, isso é o suficiente. Caso contrário, examine a saída da solicitação usando as ferramentas de desenvolvedor do seu navegador para ver o que está corrompendo a solicitação.

### Não há solicitação no Safari para usar meu autenticador

Isso não deveria mais acontecer com iOS 13, iPadOS 13 e macOS Catalina ou qualquer versão posterior.

Este é um bug do Safari em versões mais antigas. Versões mais antigas do Safari incluíam suporte para WebAuthn apenas como um recurso experimental e não estavam completamente finalizadas.

### Não consigo usar um sensor biométrico (TouchID, impressão digital, Windows Hello)

Alguns navegadores mais antigos baseados no Chromium (exceto o Google Chrome propriamente dito) não tinham suporte completo para autenticadores integrados. Eles travavam ou congelavam quando você tentava usar um. Esses problemas foram corrigidos nesses navegadores por volta de meados de 2020.

Se você estiver usando o Windows, lembre-se de que seu dispositivo DEVE ter um chip Module de Plataforma Confiável (TPM) e ele deve estar ativado na BIOS. Apenas ter um sensor biométrico compatível com o Windows Hello não resolve. Esta é uma precaução de segurança no próprio padrão WebAuthn: a informação do autenticador deve ser processada usando hardware seguro e resistente à violação para prevenir a subversão da chave (por exemplo, malware executado no computador não pode roubar a chave usada para autenticação).

Finalmente, tenha em mente que o suporte ao Windows Hello ainda está em desenvolvimento e será lançado com o Joomla 4.2.

### Se eu posso usar um autenticador de software, por que devo me preocupar com um token de hardware?

O ponto central do WebAuthn é o segredo absoluto da chave privada. Ela é conhecida apenas pelo autenticador e deve ser impossível comunicá-la ao mundo externo.

No caso de um autenticador de hardware, seja ele um dispositivo de hardware discreto ou um TPM / Enclave Seguro integrado no seu dispositivo, isso é garantido pela própria natureza desse hardware.

Um autenticador de software gera uma chave secreta e a armazena no sistema de arquivos. No entanto, ainda é um aplicativo de software regular que roda no sistema operacional regular, seja no seu telefone ou no seu computador. Como resultado, está suscetível a várias classes de ataques que podem ser usados para roubar informações de forma sorrateira (problemas de segurança no próprio software, malware usando vulnerabilidades de classe Spectre em CPUs modernas, etc).

Portanto, um autenticador de software é muito mais conveniente e seguro do que uma senha regular, mas um autenticador de hardware oferece a melhor segurança. Escolha seu autenticador com base no seu orçamento e necessidades de segurança.

Considerando que o preço de uma chave FIDO – que é compatível com o WebAuthn – é inferior a €10 na Amazon, você pode usar um autenticador de hardware na maioria dos casos práticos.

### Por que as credenciais são criptografadas no banco de dados? Isso não é exagero?

A única coisa armazenada no banco de dados é a chave pública retornada pelo autenticador quando estamos realizando a cerimônia de attestation (esse é o nome formal de registrar um autenticador de acordo com a especificação WebAuthn). Sendo uma chave pública, não precisa ser protegida contra leitura. Mesmo que um usuário não autorizado consiga ler essa informação, não conseguiria se passar pelo autenticador, por exemplo, clonando-o.

No entanto, se um usuário malicioso tivesse acesso de escrita apenas à tabela do banco de dados `#__webauthn_credentials`, sem acesso de leitura ao sistema de arquivos e sem acesso de escrita a qualquer outra tabela, ele poderia teoricamente **adicionar** seu próprio autenticador, conseguindo assim se passar pelo usuário visado no sistema. Este é um ataque muito teórico, pois eles também precisariam saber o identificador do usuário que estão atacando, o que é difícil de derivar sem algum conhecimento interno do próprio site. Além disso, ter acesso de escrita apenas a essa tabela e não ao banco de dados inteiro (caso em que poderiam criar um novo Super Usuário) é extremamente improvável. Ainda assim, estamos criptografando as credenciais para tornar impossível que mesmo esse ataque teórico tenha sucesso.

Estamos plenamente cientes de que, se um usuário tem acesso de leitura ao sistema de arquivos do servidor, ele tem acesso à chave de criptografia e às informações de conexão do banco de dados, tudo isso armazenado em configuration.php. No entanto, neste caso, você já foi hackeado: o invasor pode ler o configuration.php, portanto, ele sabe como se conectar ao seu banco de dados. Neste caso, ele pode fazer o que quiser com seu site, incluindo deletar todos os Super Usuários existentes e criar sua própria conta de Super Usuário. Portanto, não há razão para tentar abordar esta situação; você estaria totalmente comprometido (hackeado). A única coisa que pode ser uma salvação são backups regulares, testados e fora do site.

### Configurei a Autenticação de Dois Fatores, mas consigo fazer login sem fornecer minha Chave Secreta. Isso não é inseguro?

Não, é intencional e por design.

Quando adicionamos a Autenticação de Dois Fatores (TFA) no Joomla! 3.2, você só podia fazer login no seu site usando um nome de usuário e senha. Senhas podem ser roubadas ou adivinhadas. Portanto, a TFA era a única maneira de fornecer um mínimo de segurança em alvos de alto risco e alto valor. Isso foi em 2013.

O WebAuthn é uma solução de autenticação totalmente diferente que não possui os problemas de senhas fixas. Ele usa criptografia forte e hardware seguro para tornar praticamente impossível subverter as chaves criptográficas de autenticação. Também é inafiançável, ou seja, você não pode ser enganado a usá-lo em um site que se passa pelo correto, pois a credencial WebAuthn está vinculada ao nome de domínio exato para o qual foi emitida (sim, se você usa múltiplos domínios para seu site ou transfere seu site para outro domínio, você precisará registrar novamente todos os seus autenticadores WebAuthn - isso mesmo!). Como resultado, a autenticação com WebAuthn é incrivelmente segura e substitui as razões que necessitavam de TFA. Isso significa que, se você se autentica com sucesso usando WebAuthn, a chave secreta TFA não precisa ser - e portanto não é - verificada.

Em um mundo ideal, você só poderia fazer login no seu site usando WebAuthn. Esta é uma funcionalidade que estamos trabalhando para implementar e você pode não querer habilitar; afinal, se seu nome de domínio mudar ou você perder acesso ou redefinir todos os seus autenticadores WebAuthn, você ficaria trancado fora do seu site. Portanto, você ainda deve habilitar a TFA em sua conta de usuário com base no fato de que o login por senha ainda pode ser usado como alternativa para entrar em seu site e deve ser protegido contra ataques conhecidos a senhas fixas.

### A TFA não é suficiente? Por que precisamos do WebAuthn?

A TFA sozinha é suficiente na maioria dos casos, mas sofre de dois problemas.

Primeiro, ela oferece uma experiência de usuário bastante incômoda. Você precisa fornecer sua chave secreta sempre mutante junto com seu nome de usuário e senha. A maioria das pessoas usa TOTP (o PIN de seis dígitos que muda a cada 30 segundos), o que torna o login mais demorado e tende a frustrar os usuários. Usar um YubiKey é muito mais rápido, mas também mais caro e mais complicado de provisionar quando você tem mais de alguns usuários no site. Um YubiKey também tem uma vida útil esperada de cerca de 2 anos de uso diário quando gera Senhas de Uso Único (ele esgota a memória só de leitura que usa para acompanhar as assinaturas que emitiu).

Em segundo lugar, se você estiver usando TOTP, ainda estará suscetível a problemas de segurança como keyloggers, phishing e a possibilidade de que a chave secreta usada para gerar o TOTP seja roubada. Além disso, com um milhão de possibilidades e trinta segundos para experimentá-las, é concebível que um invasor possa ter sorte, pois o Joomla não bloqueia sua conta ou aplica limitações de taxa para tentativas de login falhadas. Embora essas proteções possam ser implementadas, a própria implementação poderia ser usada para criar uma situação de negação de serviço que bloqueia um usuário legítimo fora de seu site enquanto o invasor está ocupado se infiltrando nele. É um caso em que o remédio pode ser pior do que a doença.

O WebAuthn melhora muito a experiência do usuário. Grandes navegadores abraçaram o WebAuthn e oferecem uma experiência de usuário atraente, guiando os usuários no uso bem-sucedido dos autenticadores. Fazer login com WebAuthn é mais conveniente, mesmo quando comparado ao recurso de preenchimento automático de gerenciadores de senha. Com versões recentes de sistemas operacionais móveis, até mesmo essa experiência, antes um tanto confusa, está rapidamente se tornando mais fácil do que senhas e TFA jamais foram.

Onde o WebAuthn realmente brilha é na segurança. Por usar hardware seguro e validação rigorosa do nome de domínio do site, ele é praticamente imune a keyloggers, phishing e subversão de chaves. Ele ainda possui proteção embutida contra clonagem de chaves. Sim, você ainda pode perder seu hardware — mas autenticadores FIDO2, sejam dispositivos externos ou integrados, podem ser bloqueados com um PIN ou biometria. No geral, usar WebAuthn com autenticadores FIDO2 é mais resistente a roubos e perdas do que suas chaves de casa ou do carro.

## Notas do Desenvolvedor

### Botões de login extra

Os módulos de plugin e com_users agora utilizam o evento onUserLoginButtons, definido e chamado em `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, para obter as definições de quaisquer botões adicionais que precisam ser colocados após o botão de login regular.

Todos os desenvolvedores que implementam um módulo de login ou, mais genericamente, um formulário de login devem também usar o método estático público `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` para obter essas definições e renderizar esses botões para tornar seu software totalmente compatível com o Joomla 4.

Desenvolvedores que desejam implementar botões personalizados devem observar como o plugin do sistema WebAuthn implementa essa funcionalidade. Esses botões podem ser usados para implementar serviços de Single Sign-On de terceiros ou até mesmo para fazer login usando serviços de identidade de terceiros, como os oferecidos por redes sociais populares (Facebook, Google, Twitter, GitHub etc).

Esta mudança não impacta negativamente a compatibilidade retroativa. Módulos de login de terceiros e formulários de login continuarão funcionando normalmente mesmo que não implementem o recurso de botões de login extras, com a notável omissão de integrações oferecidas por esse recurso, como a própria Web Authentication. Isso quer dizer que eles não deixarão de funcionar (o que seria uma quebra de compatibilidade retroativa), mas não estarão completos em termos de funcionalidades.

### Permitindo com_ajax na página de login do backend

A página de login do Administrador coloca com_ajax na lista de permissões em AdministratorApplication para que ele possa ser usado para lidar com solicitações por usuários convidados.

Essa mudança não causa problemas de compatibilidade retroativa, desde que os desenvolvedores usem práticas sensatas e não assumam que ser chamado pelo com_ajax no backend é prova de que o usuário está logado no backend. Isso seria uma prática de segurança inadequada. A prática sensata é usar o objeto User do Joomla para detectar se é um usuário convidado e, em caso negativo, verificar se o usuário possui a permissão necessária para efetuar a ação solicitada através do com_ajax. Ou seja, se essa mudança quebrou seu código, então seu código já estava quebrado e precisava ser refeito de qualquer forma.

## Informações Adicionais

A documentação inicial deste recurso está no pull request em
[PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Traduzido por openai.com*

