<!-- Filename: J4.x:Global_Configuration / Display title: Configuração Global  -->

## Visão Geral

Durante a instalação, um site Joomla cria um arquivo chamado **configuration.php** na raiz do site. Este arquivo contém os valores das variáveis de configuração que se aplicam ao site como um todo. Exemplos incluem o nome do site e as credenciais do banco de dados que foram inseridas durante o processo de instalação. Existem muitas outras variáveis que recebem valores iniciais adequados.

O formulário de Configuração Global permite que um Super Usuário altere as variáveis de configuração para atender às necessidades do site. Além das variáveis armazenadas no configuration.php, o formulário mantém o controle de informações de Registro, Filtragem e Controle de Acesso, algumas das quais são armazenadas no banco de dados.

## Captura de Tela

O formulário de Configuração Global possui seis abas, algumas das quais contêm longas listas de parâmetros. Use o botão *Alternar Ajuda Inline* na Barra de Ferramentas para ver mais ou menos informações sobre cada parâmetro.

![Aba de configuração global do site](../../../en/images/configuration/global-configuration-site-tab.png)

Alguns parâmetros mostram ou ocultam outros parâmetros quando selecionados. Por exemplo, o botão **Site Offline** mostra mais campos quando está configurado para *Sim* do que quando está configurado para *Não*. Com a ajuda inline expandida, a maioria dos campos está suficientemente bem documentada para não precisar de explicações adicionais aqui, além de algumas notas adicionais do usuário em cada aba.

## Aba do Site

### Painel do Site

- **Nome do Site** Este é o nome do site que aparece no formulário de login do Administrador e no link do Site na barra de título. Altere conforme necessário.
- **Site Offline** Existe um [tutorial](jdocmanual?article=user/configuration/site-offline) separado sobre este item.
- **Limite Padrão da Lista** define o número máximo padrão de itens por página em visualizações de lista. Por padrão, este parâmetro é definido como 20, mas as visualizações de lista geralmente incluem uma lista suspensa para selecionar outros valores que variam de 5 a 100. Menos valores são mais rápidos de processar e envolvem menos rolagem pelo usuário.

### Painel de Metadados

- **Descrição de Metadados do Site** Esta é a descrição de metadados padrão usada se tal descrição não for especificada em um campo de Meta Descrição de artigo ou um campo de Meta Descrição de menu. Se todos os três estiverem vazios, a descrição dos metadados é omitida na saída da página. Motores de busca frequentemente usam isso para fornecer um texto descritivo para uma página. Se estiver ausente, motores de busca podem usar texto do conteúdo da página, o que pode ser inadequado. É recomendada uma descrição do propósito do site de cerca de 20 palavras.
- **Direitos de Conteúdo** define a entrada de metadados *direitos*. Se apropriado, descreva aqui quais direitos outros têm para usar este conteúdo. Esta entrada de metadados é omitida das páginas da web se esta entrada estiver em branco. Exemplo: Licença Creative Commons Attribution 4.0 International (veja o [Escolhedor de Licença Creative Commons](https://creativecommons.org/choose/)).

### Painel de SEO

SEO é a sigla para *Otimização para Mecanismos de Busca*. As configurações neste grupo alteram o formato das URLs para páginas no site e isso pode ter um efeito significativo nos rankings de busca de páginas individuais e do site como um todo. URLs SEO são mais legíveis para humanos.

**Dica** Após fazer alguma alteração nas configurações deste grupo, atualize qualquer uma das páginas do site já abertas no seu navegador (geralmente Ctrl+R ou Cmd+R farão isso). Falhar em atualizar pode significar que o formato dos links internos do site não correspondem mais ao que o Joomla está esperando e, assim, aparentar haver links quebrados.

**Dica** Evite alterar as Configurações de SEO uma vez que o site esteja estabelecido, se possível. Fazer isso pode resultar em links quebrados de outros sites e talvez uma queda temporária nos rankings de mecanismos de busca.

- **Aliases Unicode** Alterar este parâmetro não muda retroativamente os aliases, apenas altera o comportamento da geração automática de alias para futuras edições e criações de conteúdo. *Transliteração* (Não) é a configuração padrão.

### Painel de Cookies

- **Domínio do Cookie** Substitui o domínio padrão do cookie do site com o domínio adicionado aqui. A situação mais provável em que isso seria necessário é quando o site Joomla está "integrado" com outros sites (por exemplo, fórum ou e-commerce) em subdomínios do site Joomla. O domínio padrão do cookie pode ser algo como `www.exemplo.com`, mas usar `.exemplo.com` (note o ponto inicial) aqui entregará cookies válidos para qualquer subdomínio de exemplo.com.
- **Caminho do Cookie** Substitui o caminho padrão do site para o qual o cookie é válido com o caminho adicionado aqui. Isso pode ser necessário se você tiver várias instalações do Joomla em pastas irmãs.

## Aba Sistema

![Aba de sistema de configuração global](../../../en/images/configuration/global-configuration-system-tab.png)

### Painel de Depuração

Os itens neste painel são bem explicados pela ajuda embutida. No entanto, se você encontrar um problema que desabilita o acesso normal à interface do Administrador, pode ser necessário ativar a Depuração do Sistema editando o arquivo configuration.php com um editor de texto. Na maioria dos sistemas de hospedagem baseados em Linux, as permissões do arquivo estão configuradas para 444, o que impede salvar a partir de um editor de texto. Altere a permissão para 644 antes de editar. Em seguida, defina \$debug = `true`; e defina \$error_reporting = `'maximum'`; e salve. Você deve então obter um rastreamento de pilha identificando exatamente onde o problema ocorre. Você pode usar isso para buscar ajuda nos Fóruns. A maioria dos problemas surge de extensões de terceiros incompatíveis ou de problemas com o ambiente de hospedagem.

## Aba Servidor

![Guia de configuração global do servidor](../../../en/images/configuration/global-configuration-server-tab.png)

### Painel de e-mail

Um site Joomla deve ser capaz de enviar e-mails de saída. Entre outras coisas, ele enviará mensagens automáticas para o proprietário do site quando houver atualizações disponíveis. No entanto, alguns serviços de hospedagem restringem os métodos pelos quais os e-mails de saída podem ser enviados.

#### Enviar e-mail de teste

Antes do Joomla 5.3, o botão **Enviar e-mail de teste** enviava uma mensagem para o endereço configurado no campo **E-mail do remetente**. A partir da versão 5.3, o e-mail de teste é enviado diretamente para o endereço de e-mail do administrador que estiver logado.

- Primeiro, tente PHP Mail e selecione o botão *Enviar Email de Teste*. Se o email chegar, você está pronto para prosseguir. Caso contrário:
- Tente a opção Sendmail. Se isso não funcionar:
- Tente a opção SMTP. Isso deve ser configurado para um servidor de email específico. Pode ser um fornecido pelo seu serviço de hospedagem. Pode ser uma conta GMail.
- **Servidor SMTP** O nome do host do servidor SMTP (ex.: *smtp.exemplo.com*).
  - **Porta SMTP** A porta a ser usada ao conectar-se ao servidor SMTP. Normalmente será *25* quando a Segurança SMTP estiver definida como *Nenhuma*, ou *465* ou *587* quando a Segurança SMTP estiver configurada como `SSL/TLS` ou `STARTTLS`. Pergunte ao seu provedor de serviços SMTP qual porta usar.
  - **Segurança SMTP** A forma de segurança exigida pelo servidor SMTP: *Nenhuma*, *SSL/TLS* ou *STARTTLS*. O padrão é *Nenhuma*.
  - **Autenticação SMTP** Se o servidor SMTP externo requer ou não autenticação antes de aceitar emails de saída. O padrão é *Não*.
  - **Usuário SMTP** O nome de usuário a ser usado ao conectar-se ao servidor SMTP em modo SSL ou TLS. Pode ser deixado em branco se não houver autenticação SMTP.
  - **Senha SMTP** A senha a ser usada ao conectar-se ao servidor SMTP em modo SSL ou TLS. Pode ser deixada em branco se não houver autenticação SMTP.

### Usando Gmail como Servidor de Email

Se você tem uma conta Gmail funcionando, pode usar o Gmail como seu servidor de email configurando-o nas configurações globais. Na aba servidor, configure o seguinte:

- Mailer: SMTP
- Servidor SMTP: smtp.gmail.com
- Porta SMTP: 465
- Segurança SMTP: SSL/TLS
- Autenticação SMTP: Sim
- Configure as duas linhas seguintes com suas informações. Você precisa usar uma senha específica de aplicativo (ASP), descrita abaixo.
- Usuário SMTP: seu nome de usuário do Gmail
- Senha SMTP: a senha específica de aplicativo (ASP) que você gerou, descrita abaixo.

As seguintes combinações também funcionam:

- Porta SMTP: 587
- Segurança SMTP: STARTTLS
- Porta SMTP: 25
- Segurança SMTP: STARTTLS

#### Notas

- O módulo SSL não precisa ser habilitado no Apache.
- A extensão OpenSSL precisa ser habilitada no PHP. Os detalhes podem ser encontrados na [página de instalação do php.net](https://www.php.net/manual/en/openssl.installation.php).
- Se você estiver usando WAMP no Windows, o módulo openssl não é habilitado por padrão e você precisa habilitá-lo. Para fazer isso:
  - Abra o arquivo php.ini e descomente a linha `extension=php_openssl.dll` removendo o ponto e vírgula ; do início da linha.
  - Salve o arquivo php.ini e reinicie o serviço Apache.
- Se você usa verificação em duas etapas no Gmail, precisa adicionar uma nova senha em Configurações - Contas - Alterar configurações da conta - Outras configurações da Conta do Google - Segurança - Verificação em duas etapas - Gerenciar suas senhas específicas de aplicativo.
- Quando a nova Senha Específica de Aplicativo (ASP) é apresentada em grupos de quatro caracteres separados por espaços, certifique-se de **NÃO inserir os espaços** na senha SMTP nas configurações do servidor de email no Joomla.
- Senhas Específicas de Aplicativo (ASPs): Veja a página de suporte do Google sobre como [Fazer login com Senhas de Aplicativos](https://support.google.com/accounts/answer/185833).
- Verificação em Dois Passos: Veja a página de suporte do Google sobre como [Ativar a Verificação em Duas Etapas](https://support.google.com/accounts/answer/185839).

## Aba de Registro

![Aba de configuração global do site](../../../en/images/configuration/global-configuration-logging-tab.png)

Em operação normal, um site Joomla deve ter o registro desativado. Se houver problemas, você pode ativar o registro definindo o campo **Registrar Quase Tudo** para `Sim`. O campo **Registrar API Obsoleta** é realmente apenas para desenvolvedores. O campo **Caminho para a Pasta de Registro** mostra onde procurar por registros se você configurou o registro para ajudar na depuração. Os registros de erro que você encontrar lá são apenas aqueles capturados pelo Joomla. Pode haver outros erros que aparecerão apenas nos registros de erro do seu servidor.

## A guia Filtros de Texto

![Guia de configuração global do site](../../../en/images/configuration/global-configuration-filters-tab.png)

As configurações de filtro de texto serão aplicadas a todos os campos de editores de texto enviados por usuários nos grupos selecionados. Essas opções de filtragem oferecem mais controle sobre o HTML enviado pelos seus provedores de conteúdo. Você pode ser tão rigoroso ou liberal quanto necessário para atender às necessidades do seu site. A filtragem é opcional e as configurações padrão oferecem boa proteção contra marcações comumente associadas a ataques em sites.

## Aba de Permissões

![Guia de configuração global do site](../../../en/images/configuration/global-configuration-permissions-tab.png)

As permissões controlam o que os usuários em cada Grupo de Usuários podem ver e fazer. As entradas na aba de Permissões definem as permissões padrão para o site.

Há descrições abrangentes sobre o uso das configurações nesta aba e os princípios gerais de operação e configuração de permissões em um [Tutorial de Lista de Controle de Acesso](jdocmanual?article=user/users/access-control).

*Traduzido por openai.com*

