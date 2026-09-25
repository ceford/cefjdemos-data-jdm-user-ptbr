<!--
{
    "source": "https://docs.joomla.org/WebAuthn_Passwordless_Login",
    "title": "Login com chave de acesso",
    "description": " ",
    "author": ""
}
-->

## Introdução

O login com chave de acesso, anteriormente conhecido como Autenticação da
Web ou WebAuthn, permite que um usuário entre em um site com segurança sem
usar uma senha, embora ainda seja necessário um nome de usuário. Ele usa
criptografia forte de uma maneira extremamente resistente aos problemas mais
comuns das senhas:

* alguém a adivinhou (ataque de força bruta)
* alguém a interceptou (ataque de intermediário)
* alguém enganou você para que a divulgasse (ataque de phishing)
* alguém a quebrou depois de obter uma cópia dos dados do seu banco de dados
(ataques de injeção SQL)
* alguém a roubou.

O login com chave de acesso não é apenas muito seguro; ele também é muito
fácil de usar! Você não precisa mais memorizar senhas longas nem usar um
gerenciador de senhas. Tudo de que precisa é de um *autenticador*, às vezes
também chamado de *chave de acesso*.

Um autenticador pode ter muitas formas, físicas ou virtuais. Pode ser uma
chave de hardware separada conectada ao seu dispositivo via USB, Bluetooth
ou NFC. Pode ser o próprio dispositivo, desbloqueando o autenticador
integrado com um PIN, leitor de impressão digital, reconhecimento facial ou
verificação biométrica semelhante.

Esse recurso já funciona em dispositivos Android e iOS/iPadOS, e estamos
trabalhando para habilitá-lo também no Windows. Ele pode até ser o seu
celular — atualmente isso é possível com celulares Android, mas esse recurso
também está chegando aos dispositivos iOS/iPadOS.

O login com chave de acesso funciona somente por HTTPS e apenas quando o seu
site usa um certificado válido e confiável para isso. Não se preocupe: você
não precisa gastar dinheiro extra; serviços gratuitos como o Let's Encrypt
normalmente são integrados aos painéis de controle de hospedagem na web e
funcionam perfeitamente com o login com chave de acesso.

O login com chave de acesso usa criptografia de chave pública, a mesma
tecnologia comprovada que mantém seus sites seguros com HTTPS, suas
informações bancárias protegidas e assim por diante. A chave privada nunca
sai do autenticador. Seu site armazena apenas uma chave pública. Mesmo que
você sofra uma violação de dados, o invasor ficará com uma chave pública
praticamente inútil; seriam necessários milhares ou milhões de anos de CPU
para quebrá-la, em comparação com os poucos minutos ou horas necessários
para quebrar o hash de uma senha fixa que você consegue memorizar.

O login com chave de acesso é o futuro da autenticação. Fácil, seguro e sem
complicações. Tudo o que as senhas fixas não são.

A imagem a seguir mostra um dispositivo de hardware inserido na porta USB de
um computador portátil. Ele custava £15 em fevereiro de 2022.

![fotografia de um dispositivo de hardware](../../../en/images/users/passkey-login/01-hardware-device.jpg)

O login com chave de acesso usa um plugin do sistema habilitado por padrão.
Um botão **Entrar com chave de acesso** estará presente nas telas de login
padrão do Joomla 4 e posteriores, conforme ilustrado na tela de login do
Administrador:

![formulário de login seguro do administrador](../../../en/images/users/passkey-login/02-login-form.png)

## Configuração do usuário

Primeiro, o usuário deve se registrar com um Nome de usuário e uma Senha
normais. Depois de entrar, acesse o formulário do Perfil do usuário. Para
um Administrador:

- Selecione **Menu do usuário → Editar conta → Login com chave de acesso** para ver o formulário, 
  inicialmente sem nenhum autenticador registrado.
- Selecione **Adicionar nova chave de acesso**

A apresentação exata da próxima etapa depende do seu navegador.
Normalmente, você verá um alerta, uma mensagem ou uma janela solicitando que
selecione um tipo de autenticador ou, se estiver usando um autenticador de
hardware conectado ao seu dispositivo, lembrando você de pressionar o botão
no autenticador de hardware. Por motivos de segurança e praticidade, há um
intervalo de tempo relativamente curto permitido para ativar o
autenticador: 60 segundos.

![solicitação de hardware para login seguro do administrador](../../../en/images/users/passkey-login/03-hardware-prompt.png)

Depois que você desbloquear o autenticador — tocando em um botão,
escaneando sua impressão digital ou rosto, inserindo um PIN ou usando uma
combinação dos métodos acima, dependendo do seu autenticador — a mensagem
desaparecerá, o autenticador será registrado e a tela aparecerá da seguinte
forma:

![autenticador registrado no login seguro do administrador](../../../en/images/users/passkey-login/04-registered-authenticator.png)

É muito importante observar que você só pode registrar ou remover
autenticadores da sua própria conta de usuário. Por motivos de segurança,
até mesmo um Superusuário está impedido de registrar, editar ou adicionar
autenticadores em outras contas de usuário.

### Autenticadores

Você pode usar qualquer autenticador FIDO U2F ou FIDO2. O FIDO U2F é um padrão mais antigo que oferece suporte a uma seleção mais limitada e menos segura de métodos criptográficos. O FIDO2 é o padrão mais recente, que oferece suporte a métodos criptográficos muito mais seguros, incluindo a Criptografia de Curvas Elípticas, um método criptográfico que acredita-se ser resistente até mesmo à computação quântica (se e quando ela se tornar uma realidade prática). Além disso, os autenticadores FIDO2 podem ser configurados para ter proteções adicionais, como um PIN ou um controle biométrico (por exemplo, leitura de impressão digital), o que significa que, mesmo que você perca a posse física do próprio autenticador, quem o encontrar não poderá fazer login nos seus sites.

Se você está procurando comprar um autenticador de hardware, pode procurar por
"FIDO2" no seu marketplace favorito, como a Amazon. Há uma grande
variedade à sua disposição.

Você também pode usar uma chave FIDO de software, como o Krypton, como seu
autenticador.

Muitos dispositivos têm autenticação integrada compatível com FIDO2:

- O Windows 10 e 11 têm o Windows Hello com um PIN, leitor de impressão digital,
  câmera de reconhecimento facial ou uma combinação de chave de hardware e PIN.
- O macOS tem TouchID em todos os laptops com o chipset T2 ou baseados em
  Apple Silicon que usam o sensor TouchID integrado, bem como em todos os
  desktops baseados em Apple Silicon que usam o novo teclado Apple de alumínio
  com leitor de impressão digital.
- O iOS / iPadOS tem TouchID em todos os dispositivos com leitor de impressão
  digital e FaceID em todos os dispositivos mais recentes com uma câmera
  infravermelha de projeção de pontos para o FaceID.
- Alguns dispositivos Android têm um leitor de impressão digital ou uma câmera
  de reconhecimento facial. Eles também podem funcionar como autenticadores
  FIDO2, no Android 9 ou posterior usando pelo menos o Google Chrome.
- Outros dispositivos também podem estar disponíveis. Por exemplo, telefones
  Android que usam
  [caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### Navegadores compatíveis com login por chave de acesso

Na prática, se o seu sistema operacional e navegador foram lançados
depois de meados de 2020, você não deverá ter problemas. Apenas alguns
navegadores muito incomuns ainda não oferecem suporte ao login por chave de acesso.

## Autenticação

Para fazer login, você deve inserir seu nome de usuário no campo Nome de usuário do formulário de login. Não é necessário inserir sua senha, mas, se o navegador fizer isso por você, basta deixá-la. A senha NÃO é enviada ao servidor quando o formulário é enviado pelo botão Autenticação da Web.

Consequentemente, você pode fazer login usando seu nome de usuário e senha ou
seu nome de usuário e uma chave de acesso.

## Como desativar o plugin

Se você não deseja permitir o login por chave de acesso, basta acessar a lista de plugins, localizar o plugin **System - Passkey (Passwordless) Login** no grupo Sistema e desativá-lo. Não há parâmetros a configurar.

## Requisitos do servidor

Para que o login por chave de acesso funcione, as seguintes condições prévias devem ser atendidas:

- HTTPS com um certificado válido e assinado. A maioria dos hosts permite usar certificados gratuitos emitidos pela Let's Encrypt. Eles funcionam perfeitamente com o login por chave de acesso.
- A extensão OpenSSL para PHP deve estar instalada e habilitada.
- A extensão GMP ou a extensão BCmath do PHP deve estar instalada e habilitada (qualquer uma delas é suficiente).
- A biblioteca Sodium deve estar habilitada, idealmente; ela permite o uso de Criptografia de Curvas Elípticas em autenticadores FIDO2 compatíveis que, como dissemos, usam o método criptográfico mais seguro.

## Perguntas frequentes e solução de problemas

### Não consigo ver o botão *Entrar com chave de acesso*

Você não está acessando seu site por HTTPS. O login por chave de acesso só está disponível para sites HTTPS com um certificado válido. Essa é uma precaução de segurança incorporada ao padrão de login por chave de acesso. O plugin verifica se o site é acessado por HTTPS usando a classe Uri do Joomla. Em casos raros nos quais o servidor informa incorretamente o protocolo, talvez você não veja o botão, mesmo que seu site (afirme estar) em HTTPS. O mesmo se aplica se você tiver editado o arquivo configuration.php e configurado o parâmetro opcional \$live_site com um prefixo de protocolo http:// em vez de https://.

Observe também que módulos e componentes de login de terceiros que implementam
seu próprio formulário de login talvez ainda não exibam esses botões. Adicionamos
uma nova infraestrutura para oferecer suporte a eles, de forma semelhante ao que
tivemos que fazer no Joomla! 3.2 para oferecer suporte à autenticação de dois fatores.

### Ainda preciso fornecer um nome de usuário. O login com Passkey não deveria eliminar os nomes de usuário?

Na verdade, não. A especificação atual do login com Passkey não fornece
gerenciamento de identidade. Os navegadores da Web exigem que enviemos a eles uma lista de
chaves públicas de login com Passkey aceitáveis durante a fase de login. Isso significa que
precisamos do seu nome de usuário para obtê-las.

Dito isso, usar o login com Passkey finalmente deixa claro que os nomes de usuário *não devem
ser considerados segredos*. Eles são considerados informações públicas que
podem ser livremente transmitidas a um adversário, assim como as chaves públicas
armazenadas no banco de dados do site. O único segredo é armazenado no próprio
autenticador e nunca sai dele!

### Registrei um autenticador, mas ao tentar fazer login sou informado de que não registrei nenhum. Isso é um bug?

É um bug, mas não no próprio plugin de login com Passkey.

Um ou mais plugins do seu site geram Notices, Warnings ou Errors do PHP,
corrompendo assim a resposta enviada pelo seu servidor. Como resultado, o
JavaScript da página não consegue analisar a resposta do servidor e não sabe ao certo
se algum autenticador foi registrado pelo usuário.

Acesse o backend do seu site, Sistema, Configuração global e defina Relatório de erros como Nenhum. Na maioria dos casos de problemas com plugins do núcleo
e de terceiros, isso é suficiente. Caso contrário, examine a saída da solicitação usando as ferramentas de desenvolvimento do seu navegador para ver o que está corrompendo a solicitação.

### Não há nenhum prompt no Safari para usar meu autenticador

Isso não deveria mais acontecer com o iOS 13, iPadOS 13 e macOS
Catalina ou qualquer versão posterior.

Esse é um bug do Safari em versões mais antigas do Safari. As versões mais antigas do
Safari incluíam suporte ao login com Passkey apenas como um recurso experimental, e
ele ainda não estava totalmente concluído.

### Não consigo usar um sensor biométrico (TouchID, impressão digital, Windows Hello)

Alguns navegadores mais antigos baseados no Chromium (exceto o Google Chrome propriamente dito) não tinham
suporte completo para autenticadores integrados. Eles travavam ou paravam de responder
quando você tentava usar um deles. Esses problemas foram corrigidos nesses navegadores
por volta de meados de 2020.

Se você estiver usando o Windows, lembre-se de que seu dispositivo DEVE ter um
chip Trusted Platform Module (TPM), que deve estar habilitado no BIOS.
Ter apenas um sensor biométrico compatível com o Windows Hello não será suficiente. Essa é uma precaução de segurança do próprio padrão de login com Passkey:
as informações do autenticador devem ser processadas usando hardware seguro e resistente a
adulterações para impedir a subversão de chaves (por exemplo, um malware
em execução no computador não pode roubar a chave usada para autenticação).

Por fim, lembre-se de que o suporte ao Windows Hello ainda está sendo
desenvolvido e será lançado com o Joomla 4.2.

### Se posso usar um autenticador de software, por que deveria me preocupar com um token de hardware?

O ponto central do login com Passkey é o sigilo absoluto da chave privada. Ela
só é conhecida pelo autenticador e deve ser impossível
comunicá-la ao mundo externo.

No caso de um autenticador de hardware, seja um dispositivo de hardware
independente ou um TPM / Secure Enclave integrado ao seu dispositivo, isso é garantido
pela própria natureza desse hardware.

Um autenticador de software gera uma chave secreta e a armazena no sistema de arquivos. No entanto, ele ainda é um aplicativo de software comum que
é executado dentro do seu sistema operacional habitual, seja o do seu telefone ou o do seu computador. Como resultado, ele é suscetível a várias classes de ataques
que podem ser usadas para roubar informações sub-repticiamente (problemas de segurança
no próprio software, malware que usa vulnerabilidades da classe Spectre em
CPUs modernas etc.).

Portanto, um autenticador de software é muito mais conveniente e seguro do que uma
senha comum, mas um autenticador de hardware oferece a melhor segurança.
Escolha seu autenticador com base no seu orçamento e nas suas necessidades de segurança.

Considerando que o preço de uma chave FIDO (compatível com
o login com Passkey) é inferior a €20 na Amazon, você pode usar um autenticador de hardware na
maioria dos casos práticos de uso.

### Por que as credenciais são criptografadas no banco de dados? Isso não é um exagero?

A única coisa armazenada no banco de dados é a chave pública retornada pelo
autenticador quando realizamos a cerimônia de atestação (esse é o nome
formal do registro de um autenticador de acordo com a especificação de login
com Passkey). Por ser uma chave pública, ela não precisa ser protegida contra
leitura. Mesmo que um usuário não autorizado conseguisse ler essas
informações, não seria capaz de personificar o autenticador, por exemplo,
clonando-o.

No entanto, se um usuário mal-intencionado tivesse acesso de escrita apenas à
tabela `#__webauthn_credentials` do banco de dados, sem acesso de leitura ao
sistema de arquivos e sem acesso de escrita a qualquer outra tabela, ele
poderia, em teoria, **adicionar** seu próprio autenticador e, portanto, ser
capaz de personificar o usuário visado no sistema. Esse é um ataque bastante
teórico, pois ele também precisaria saber o identificador do usuário que está
atacando, algo mais difícil de descobrir sem algum conhecimento interno do
próprio site. Além disso, ter acesso de escrita somente a essa tabela, e não ao
banco de dados inteiro (caso em que ele poderia criar um novo Superusuário), é
extremamente improvável. Ainda assim, criptografamos as credenciais para
tornar impossível até mesmo o sucesso desse ataque inteiramente teórico.

Temos plena consciência de que, se um usuário tiver acesso de leitura ao
sistema de arquivos do servidor, ele terá acesso à chave de criptografia e às
informações de conexão com o banco de dados, todas armazenadas em
configuration.php. No entanto, nesse caso, você já foi invadido: o invasor
pode ler o configuration.php e, portanto, sabe como se conectar ao seu banco
de dados. Nesse caso, ele pode fazer o que quiser no seu site, inclusive
excluir todos os Superusuários existentes e criar sua própria conta de
Superusuário. Portanto, não há motivo para tentar lidar com essa situação;
você estaria totalmente comprometido (invadido). A única coisa que poderia
salvá-lo seriam backups regulares, testados e armazenados fora do site.

### Configurei a autenticação de dois fatores, mas estou conectado sem fornecer minha chave secreta. Isso não é inseguro?

Não, isso é intencional e faz parte do projeto.

Quando adicionamos a autenticação de dois fatores (TFA) ao Joomla! 3.2, você
só podia fazer login no seu site usando um nome de usuário e uma senha. As
senhas podem ser roubadas ou adivinhadas. Portanto, a TFA era a única forma
de fornecer um nível mínimo de segurança em alvos de alto risco e alto valor.
Isso foi em 2013.

O login com Passkey é uma solução de autenticação completamente diferente que não tem nenhum
dos problemas das senhas fixas. Ele usa criptografia forte e hardware seguro
para tornar praticamente impossível subverter as chaves criptográficas de
autenticação. Ele também não é suscetível a phishing, ou seja, você não pode
ser enganado a usá-lo em um site que esteja se passando por outro, pois a
credencial de login com Passkey está vinculada ao nome de domínio exato para o
qual foi emitida (sim, se você usar vários domínios para o seu site ou
transferir seu site para outro domínio, precisará registrar novamente todos
os seus autenticadores de login com Passkey — é isso mesmo!). Como resultado,
a autenticação com login por Passkey é incrivelmente segura e supera os
motivos que tornaram a TFA necessária. Isso significa que, se você se
autenticar com sucesso usando o login com Passkey, a chave secreta da TFA não
precisa ser — e, portanto, não é — verificada.

Em um mundo ideal, você só poderia fazer login no seu site usando o login
com Passkey. Esse é um recurso no qual estamos trabalhando, e talvez você
não queira ativá-lo; afinal, se o nome de domínio mudar ou você perder o
acesso aos seus autenticadores de login com Passkey, ou redefinir todos eles,
ficará impedido de acessar o site. Portanto, você ainda deve ativar a TFA na
sua conta de usuário, considerando que o login com senha ainda pode ser usado
como alternativa para acessar o site e precisa ser protegido contra ataques
conhecidos a senhas fixas.

### A TFA não é boa o suficiente? Por que precisamos do login com Passkey?

A TFA, por si só, é boa o suficiente na maioria dos casos, mas apresenta
dois problemas.

Primeiro, ela oferece uma experiência de usuário bastante inconveniente. Você
precisa fornecer sua chave secreta, que muda constantemente, junto com seu
nome de usuário e senha. A maioria das pessoas usa TOTP (o PIN de seis dígitos
que muda a cada 30 segundos), o que torna o login mais lento e tende a
frustrar os usuários. Usar uma YubiKey é muito mais rápido, mas também é mais
caro e mais complicado de provisionar quando você tem mais do que alguns
usuários no site. Uma YubiKey também tem uma vida útil esperada de cerca de
2 anos de uso diário ao gerar Senhas de Uso Único (ela esgota a memória de
gravação única usada para acompanhar as assinaturas que emitiu).

Segundo, se você usa TOTP, ainda está suscetível a problemas de segurança
como keyloggers, phishing e à possibilidade de a chave secreta usada para
gerar o TOTP ser roubada. Além disso, com um milhão de possibilidades e trinta
segundos para tentar, é concebível que um invasor tenha sorte, já que o Joomla
não bloqueia sua conta nem emprega limitação de taxa para tentativas de login
malsucedidas. Embora essas proteções pudessem ser implementadas, a própria
implementação poderia ser abusada para criar uma situação de negação de
serviço que bloqueasse um usuário legítimo fora de seu site enquanto o invasor
estivesse ocupado infiltrando-se nele. É um caso em que o remédio é pior do
que a doença.

O login com Passkey melhora consideravelmente a experiência do usuário. Os
principais navegadores adotaram o login com Passkey e oferecem uma experiência
de usuário convincente, orientando os usuários a usar autenticadores com
sucesso. Fazer login com Passkey é mais conveniente até mesmo quando comparado
ao uso do preenchimento automático de um gerenciador de senhas. Com as versões
recentes dos sistemas operacionais móveis, até mesmo essa experiência, que antes
era um pouco confusa, está rapidamente se tornando mais fácil do que as senhas
e a TFA jamais foram.

É na área de segurança que o login com Passkey realmente se destaca. Por usar
hardware seguro e uma validação robusta do nome de domínio do site, ele é
praticamente imune a keyloggers, phishing e comprometimento de chaves. Ele
também conta com proteção integrada contra clonagem de chaves. Sim, você ainda
pode perder seu hardware — mas os autenticadores FIDO2, sejam dispositivos
externos ou integrados, podem ser bloqueados com um PIN ou biometria. No geral,
usar o login com Passkey com autenticadores FIDO2 é mais resistente a roubo e
perda do que as chaves da sua casa ou do seu carro.

## Notas para desenvolvedores

### Botões de login adicionais

O módulo de plugin e o com_users agora usam o evento onUserLoginButtons,
definido e chamado em
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, para recuperar as
definições de quaisquer botões adicionais que precisem ser colocados após o
botão de login normal.

Todos os desenvolvedores que implementam um módulo de login ou, de forma mais
geral, um formulário de login também devem usar o método estático público
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` para recuperar essas
definições e renderizar esses botões, tornando seus softwares totalmente
compatíveis com o Joomla 4.

Os desenvolvedores que desejarem implementar botões personalizados devem
observar como o plugin de sistema de login com Passkey implementa essa
funcionalidade. Esses botões podem ser usados para implementar serviços de
login único de terceiros ou até mesmo para fazer login usando serviços de
identidade de terceiros, como os oferecidos por redes sociais populares
(Facebook, Google, Twitter, GitHub etc.).

Essa alteração não afeta negativamente a compatibilidade com versões
anteriores. Os módulos e formulários de login de terceiros continuarão
funcionando normalmente mesmo que não implementem o recurso de botões de login
adicionais, com a notável ausência das integrações proporcionadas por esse
recurso, como a própria Autenticação da Web. Em outras palavras, eles não
deixarão de funcionar (o que seria uma quebra de compatibilidade), mas não
terão todos os recursos.

### Permitir com_ajax na página de login do backend

A página de login do Administrador permite com_ajax na
AdministratorApplication, para que ele possa ser usado para tratar solicitações
de usuários convidados.

Essa alteração não causa problemas de compatibilidade com versões anteriores,
desde que os desenvolvedores usem práticas sensatas e não presumam que ser
chamado por com_ajax no backend seja prova de que o usuário está conectado ao
backend. Essa seria uma prática de segurança inadequada. A prática sensata é
usar o objeto User do Joomla para detectar se o usuário é um convidado e, caso
não seja, verificar se ele tem a permissão necessária para executar a ação
solicitada por meio do com_ajax. Em outras palavras, se essa alteração
quebrou seu código, então seu código já estava quebrado e precisava ser
reelaborado de qualquer maneira.

## Mais informações

A documentação inicial desse recurso está na solicitação de pull em
[PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Traduzido por openai.com*