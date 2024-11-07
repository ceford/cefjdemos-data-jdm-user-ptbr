<!-- Filename: J4.x:Multi-factor_Authentication / Display title: Autenticação Multi-fator   -->

## Introdução

O sistema de Autenticação Multifator do Joomla! é baseado no Akeeba Loginguard e grande parte desta documentação foi derivada com permissão da Akeeba.  

## O que ele faz?

Ele adiciona múltiplos métodos opcionais de Verificação em Duas Etapas para login no Joomla!. Após fazer login apenas com seu nome de usuário e senha, você é solicitado a fornecer sua verificação de segundo passo, por exemplo, um código gerado pelo Google Authenticator. Até que você forneça uma verificação de segundo passo correta, não poderá acessar nenhuma página do site. Você sempre será redirecionado para a página de "login cativo". Isso é semelhante ao que o Google faz quando você tenta fazer login no GMail.

Isso difere do método original de autenticação de dois fatores do Joomla!, que exigia que o segundo fator de autenticação (por exemplo, o código gerado pelo Google Authenticator) fosse inserido juntamente com o nome de usuário e a senha.

As vantagens da Verificação em Duas Etapas são:

- É menos confuso para o usuário. Não há mais necessidade do campo "Chave Secreta", que confunde os usuários.
- Pode funcionar com métodos de login sem senha, como login social (por exemplo, Facebook), token de hardware seguro, SSO (single sign-on), etc. Esclarecimento: a Verificação em Duas Etapas pode ser configurada para ser solicitada após um usuário fazer login usando um método sem senha. Não implementa métodos de login sem senha.
- Possui melhor controle de acesso. Você pode configurar Opções do Usuário para Exigir ou Desativar a Autenticação Multifatorial por grupo de usuário.
- Permite métodos de autenticação alternativos em uma única conta. Você pode ter vários métodos de autenticação em sua conta. Por exemplo, você pode configurar um aplicativo Google Authenticator e um YubiKey.
- Suporta métodos que não exigem a entrada de um código. Por exemplo, dongles FIDO2, verificação biométrica etc. Estes precisam interagir com o navegador e/ou o sistema operacional por meio de APIs nativas do HTML5.
- Suporta métodos que exigem interação do usuário. Por exemplo, o envio de um código por mensagem push, SMS ou e-mail. Esses métodos requerem o conhecimento de qual usuário está sendo autenticado antes de enviar o código de autenticação para o usuário.
- É gratuito. Ao contrário de serviços de terceiros que fornecem autenticação multifatorial, você não precisa pagar uma taxa de configuração inicial ou uma taxa de manutenção mensal/anual para cada site ou usuário que utilize a Verificação em Duas Etapas. O software é gratuito.

## Como funciona

Você faz login no seu site normalmente, por exemplo, fornecendo um nome de usuário e senha. É importante notar que você não precisa inserir suas credenciais de autenticação de segundo passo nesta etapa.

O sistema detecta que você está agora logado, mas não realizou a autenticação de segundo passo. Ele armazena a URL que você deveria ver e imediatamente o redireciona para a página de login cativo. Qualquer tentativa de navegar para uma página diferente resultará no aparecimento da página cativa.

Módulos no seu site podem conter informações privilegiadas. Para garantir a confidencialidade, os módulos são desativados à força no momento da renderização. Isso significa que nenhuma posição de módulo será renderizada na página. Lembre-se disso caso você perceba que o cabeçalho ou outras áreas chave do design do seu site estão ausentes na página de login cativo.

Observe que plugins, por outro lado, NÃO são desativados. Isso ocorre tanto porque o Joomla torna extremamente difícil remover plugins específicos uma vez que eles estão carregados, quanto porque a maioria dos plugins realiza funcionalidades críticas no seu site.

Após fornecer sua verificação de segundo passo, uma sinalização é definida na sessão do usuário, indicando que você está totalmente autorizado a usar o site. Além disso, você será redirecionado para a URL que foi armazenada logo após o seu login inicial.

## Autenticação em Duas Etapas versus Logins WebAuthn

Fazer login com WebAuthn é a opção mais segura. Você só fornece um nome de usuário, que deve ser considerado uma informação pública e sem privilégios. O site cria um desafio criptográfico que é assinado pelo navegador usando hardware seguro — um token de hardware seguro externo ou o Trusted Platform Module / Secure Enclave do seu dispositivo — e retorna ao servidor. O servidor valida a assinatura. Essa validação usa criptografia de chave pública, com o site armazenando apenas a chave pública. Isso torna o login virtualmente imune a phishing e extremamente seguro. Se você usar isso, não precisa de um segundo fator de autenticação — mas, se realmente quiser, pode usar o WebAuthn para isso também.

Excluindo o uso de quaisquer métodos de login federados (como fazer login com sua conta de mídia social, um serviço de Single Sign-On, um servidor LDAP etc.), um login convencional com nome de usuário + senha não é tão seguro quanto um login com WebAuthn. Digitar um nome de usuário e uma senha pode ser interceptado, roubado ou adivinhado. Isso torna confiar apenas em um nome de usuário e senha muito problemático.

Para a autenticação multifatorial, você só fornece seu nome de usuário e senha. Um ataque de phishing bem-sucedido só obteria esse primeiro fator de autenticação, mas não o seu segundo fator de autenticação. Após um login bem-sucedido, você é apresentado a uma página restritiva. Você não pode fazer mais nada no site até fornecer seu segundo fator. Como o segundo fator é apresentado em uma página própria, ele pode ser interativo (por exemplo, WebAuthn), assíncrono (por exemplo, recebendo um OTP por e-mail, mensagem de texto ou notificação push) ou iniciado pelo usuário (por exemplo, um TOTP ou um OTP do Yubikey). Ainda melhor, um usuário pode ter vários métodos de segundo fator habilitados em sua conta para evitar bloqueios acidentais no site. Por exemplo, você pode estar usando WebAuthn com um dongle de hardware seguro externo como seu segundo fator primário e mais seguro. Você também pode ter um TOTP regular configurado para o caso de perder o dongle ou esquecer de levá-lo com você. Alguns métodos de segundo fator permitem várias instâncias, por exemplo, você pode ter múltiplos autenticadores WebAuthn para poder usar o autenticador embutido em seu computador com Windows, seu iPhone e seu tablet Android sem precisar lembrar de embalar um dongle de hardware e adaptadores sempre que sair da sua mesa.

Vamos recapitular. Das opções mais seguras para as menos seguras, temos:

- WebAuthn como seu método de login primário com Autenticação Multifatorial secundária.
- WebAuthn como seu único método de login.
- Nome de usuário e senha como seu método de login primário com Autenticação Multifatorial secundária.
- Apenas um nome de usuário e senha como seu único método de login.

## Plugins

Cada um dos fatores na Autenticação Multifator é implementado via plugins. Eles podem ser ativados ou desativados conforme necessário. E novos podem ser adicionados quando surgem novos métodos. Os plugins fornecidos com o núcleo do Joomla incluem:

- **Código de Verificação**: códigos de verificação de seis dígitos gerados por um aplicativo autenticador (Google Authenticator, Authy, LastPass Authenticator, etc.), um gerenciador de senhas (1Password, BitWarden, Keeper, KeePassXC, Strongbox, etc.) ou, em alguns casos, pelo navegador.

- **YubiKey**: Permite que os usuários do seu site utilizem a Autenticação Multifator usando um token de hardware seguro YubiKey. Os usuários precisam de sua própria YubiKey disponível em www.yubico.com.

- **Autenticação pela Web**: suportada por todos os navegadores modernos. A maioria dos navegadores oferece autenticação específica do dispositivo protegida por uma senha e/ou biometria (sensor de impressão digital, reconhecimento facial, etc.).

- **Código de Autenticação por Email**: Utilize códigos de segurança de seis dígitos com tempo limitado enviados por email. A configuração padrão é 2 minutos.

- **Código Fixo**: este é destinado para testes e ilustrações e é desativado por padrão. Não deve ser ativado em um site de produção.

Observe que há um plugin separado **Sistema - WebAuthn Login sem Senha** para lidar com login a partir do botão Autenticação pela Web no formulário de login.

## Opções de Usuários

O formulário Opções de Usuários possui um formulário de Autenticação Multifatorial para configurar como a Autenticação Multifatorial funciona no Joomla. Selecione o botão Alternar Ajuda Inline para obter informações sobre cada opção.

![formulário de opções de usuários autenticação multifatorial](../../../en/images/users/users-configuration-mfa.png)

## Perfil do Usuário

O formulário Administrador / Usuários: Editar Perfil tem abas separadas para Login WebAuthn e Autenticação Multifator, mas esta última é visível apenas para o proprietário da conta. Mesmo os Super Usuários não veem essa aba para outros usuários.

O formulário Site / Editar Seu Perfil tem as abas do formulário backend dispostas uma acima da outra, o que pode ser confuso porque a Autenticação Web aparece duas vezes, primeiro para login sem senha e depois para Autenticação Multifator. A ilustração a seguir mostra a parte da Autenticação Multifator do formulário após a criação de um método. Isso define automaticamente o recurso como Habilitado e mostra a opção de criar Códigos de Backup.

![vista do site do formulário de autenticação multifator do usuário](../../../en/images/users/multi-factor-authentication-site-profile.jpg)

Como mencionado acima, você pode experimentar cada um selecionando o botão + Adicionar..., mas selecione Cancelar no formulário subsequente se decidir não prosseguir.

*Traduzido por openai.com*

