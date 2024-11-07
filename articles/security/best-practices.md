<!-- Filename: https://magazine.joomla.org/all-issues/april-2021/best-practices-to-secure-your-joomla-website / Display title: Melhores Práticas  -->

## Artigos de Segurança

Há um número significativo de artigos disponíveis sobre segurança no Joomla que remontam a muitos anos. Infelizmente, muitos deles estão desatualizados e, talvez, enganem. Por exemplo, há uma série de artigos de Lista de Verificação de Segurança que não são todos realmente sobre segurança.

Este artigo é baseado em um artigo da Revista da Comunidade Joomla! por Ahmad Moussa na edição de abril de 2021.

## Melhores Práticas para Proteger seu Site Joomla

O Joomla Content Management System (CMS) é amplamente utilizado na internet devido à sua facilidade de uso e popularidade, sendo o segundo maior CMS, com mais de 110 milhões de downloads. No entanto, apesar de sua popularidade, o Joomla, assim como todos os outros sites, aplicativos, sites de comércio eletrônico ou outros CMSs, contém riscos de segurança. Você não pode escapar deles, mas, felizmente, tomar as precauções certas desde o início pode garantir que seu site esteja protegido.

Compilamos este guia abrangente e passo a passo sobre a segurança do Joomla para você. Ele visa fornecer etapas fáceis de seguir para melhorar a segurança do seu site Joomla. Portanto, se garantir a segurança do seu site Joomla contra todos os ataques está na sua agenda, então vale a pena ler. Todas as dicas mencionadas neste artigo são para garantir que você esteja implementando as melhores práticas de segurança e manutenção para proteger seus ativos mais importantes online.

## 1. Escolha Nomes de Usuário e Senhas Inteligentes

Seja inteligente ao escolher os nomes de usuário e senhas do administrador do Joomla. Não use "admin" como seu nome de usuário e escolha uma senha complexa. Esta é provavelmente uma das melhores maneiras de reforçar a segurança do seu Joomla e, ironicamente, é uma das mais fáceis.

Usar uma senha segura é necessário para uma boa segurança no Joomla. Certifique-se de que sua senha de login seja longa o suficiente (8-14 caracteres) e inclua alfabetos, números e símbolos. Como as senhas diferenciam maiúsculas de minúsculas, usar tanto letras maiúsculas quanto minúsculas as torna ainda mais fortes. Além disso, adquira o hábito de mudar a senha de administrador pelo menos uma vez por mês.

## 2. Pratique o Princípio do Menor Privilégio

Certifique-se de entender os três grupos de permissões distintos:

1. Gerentes: Têm o menor acesso ao backend do Joomla. Podem criar e editar categorias e artigos. Têm acesso ao gerenciador de mídia e podem fazer upload e remover mídia. Não podem instalar ou remover extensões.
2. Administradores: Têm todos os direitos dos Gerentes, junto com algumas permissões adicionais. Têm acesso ao Gerenciamento de Usuários, Gerenciador de Menus e Gerenciador de Extensões. Não podem acessar o menu de Configuração Global do Joomla.
3. Super Usuários: Têm acesso total ao Backend do Joomla. Têm todos os direitos dos Gerentes e Administradores, além de acesso à Configuração Global. Somente Super Usuários podem adicionar, editar e remover Super Usuários.

É importante que você distribua cuidadosamente esses papéis para o seu grupo de usuários. Qualquer pessoa com a função de Super Usuário pode realizar qualquer ação dentro do sistema Joomla. Se você delegar tarefas a um membro da equipe que requer menos permissões, atribua ao membro a conta com a descrição de acesso mínimo.

## 3. Use Autenticação Multimodalidade do Joomla

É altamente recomendável ativar a autenticação multimodalidade do Joomla, que adiciona uma camada extra de segurança ao seu site Joomla. Tradicionalmente, quando você deseja fazer login no seu site, precisa fornecer seu nome de usuário e senha para se identificar no sistema. O maior problema com essa abordagem é que seu nome de usuário e senha podem ser roubados ou adivinhados. Portanto, os plugins de autenticação multimodalidade do Joomla podem proteger seu site contra hackers, adicionando uma segunda camada de segurança. Existem cinco métodos diferentes para você escolher após inserir seu nome de usuário.

## 4. Restringir Acesso ao Backend Administrativo do Joomla

É sensato limitar o acesso ao backend administrativo do Joomla usando filtragem de IP, uma vez que é um recurso sensível. Isso também pode ser feito para outras pastas sensíveis do Joomla, seguindo os passos mencionados abaixo:

Passo 1: Primeiramente, crie um arquivo .htaccess se ele ainda não estiver presente no diretório que você deseja proteger.

Passo 2: Adicione o seguinte código ao arquivo .htaccess:
```
Order Deny, Allow
Deny from all
Allow from xx.xx.xx.xx
```

Passo 3: Insira o endereço IP dedicado do qual você deseja permitir o acesso no lugar de xx.xx.xx.xx.

Mais informações sobre como restringir o acesso a diretórios por endereço IP usando
htaccess podem ser encontradas neste artigo da Documentação do Joomla!. Você também pode usar extensões de segurança que podem restringir o acesso ao backend administrativo do Joomla usando o recurso de filtragem de IP e incluem muitos outros recursos que fortalecem a segurança do seu site Joomla.

## 5. Utilize Conexões FTP Seguras

Certifique-se de que as conexões utilizadas para acessar os arquivos do site Joomla sejam seguras. Você deve usar a criptografia SFTP se seu serviço de hospedagem oferecer essa opção, ou SSH. Se estiver utilizando um cliente FTP, o porto padrão para SFTP geralmente é 22.

Alguns clientes de FTP armazenam senhas em texto simples ou codificadas no seu computador. Mesmo algumas senhas codificadas podem ser convertidas de volta para o formato original. Recomendamos fortemente que você não salve senhas de FTP no cliente para evitar ser hackeado.

## 6. Faça Backups Regulares

Economize tempo se preparando para o pior cenário em caso de ataque ao seu site. Portanto, é aconselhável criar um backup completo e funcional do seu site Joomla. Um backup funcional pode restaurar seu site em minutos após um ataque cibernético.

Os dois principais componentes de um backup são:

- O núcleo do Joomla e outros arquivos importantes
- O Banco de Dados

Além disso, os métodos de backup podem ser flexíveis. Você pode fazer um backup de duas formas – Manual e Automatizada, conforme descrito abaixo:

### Processo Manual

O backup manual do site Joomla precisa de dois componentes: arquivos e o banco de dados. Para fazer backup dos seus arquivos e pastas do Joomla, use um utilitário de FTP ou o gerenciador de arquivos, caso você use hospedagem de terceiros.

Os clientes de FTP podem baixar todos os arquivos um por um para sua máquina local. No entanto, esse processo pode ser lento. Uma vez que os arquivos tenham sido baixados, compacte a pasta em um único arquivo zip e proteja-o com senha.

Enquanto isso, o banco de dados pode ser feito backup exportando uma cópia do banco de dados para o seu computador. Faça login no banco de dados que você deseja exportar usando o phpMyAdmin. Clique no nome do banco de dados no lado esquerdo da página. Depois de clicar em seu banco de dados do Joomla, você verá uma tela com uma guia rotulada como "Exportar". Selecione a guia Exportar e clique no botão rotulado como "Ir". Em seguida, salve-o em um local seguro.

### Processo Automatizado

Para backup automatizado, uma extensão do Joomla como o Akeeba Backup pode ajudar. Instale a extensão Akeeba Backup no seu site Joomla após baixar do site oficial do desenvolvedor. Após a conclusão da instalação, acesse o Painel da extensão e faça backup do seu site. Quando o backup estiver completo, você será redirecionado para uma página. Aqui, clique em “Gerenciar Backups”. Isso abrirá uma página contendo todos os backups. Você pode baixar o backup daqui e salvá-lo localmente.

## 7. Mantenha seu site Joomla atualizado

Atualizar seu site Joomla pode fornecer segurança e estabilidade ao site. Além disso, nem todas as atualizações são atualizações completas de versão do site; algumas atualizações podem ser menores e apenas correções de bugs, enquanto outras são atualizações de versão.

O Joomla possui uma equipe de segurança dedicada, conhecida por lançar patches rapidamente. Não corrigir seu site Joomla pode torná-lo vulnerável a ataques.

Para verificar seu site para atualizações, você pode fazer o seguinte:

Passo 1: Faça login em seu site Joomla como administrador

Passo 2: Em seguida, navegue até Componentes>Atualização do Joomla

Passo 3: Agora, o Joomla verificará se há alguma atualização disponível. Se mostrar uma nova atualização, simplesmente clique na opção “Instalar a Atualização”.

Antes de atualizar para uma versão mais recente do Joomla, algumas coisas devem ser verificadas:

- Atualização de Modelos: Verifique se os seus modelos Joomla são compatíveis com a nova versão do Joomla. Caso contrário, peça ao autor do modelo para atualizá-lo ou use uma alternativa.
- Atualização de Extensões: Inspecione e certifique-se de que todas as extensões do Joomla sejam compatíveis com a nova versão do Joomla. Remova todas aquelas que não forem compatíveis. Para atualizar as extensões, navegue até Extensões>Gerenciar e clique em atualizar.
- Limpar Cache: Após atualizar para uma versão mais recente do Joomla, limpe o cache do seu site Joomla. Isso pode ser feito usando a funcionalidade incorporada do Joomla.

## 8. Use Extensões e Modelos de Terceiros Confiáveis:

É recomendado usar um número mínimo de extensões no seu site para obter o nível ótimo de segurança no Joomla. O uso de extensões ou modelos de terceiros não confiáveis pode apresentar vulnerabilidades e afetar o desempenho do seu site Joomla. Nem todas as extensões de terceiros estão livres de problemas; se você puder evitar uma extensão de terceiros, faça isso! Escolha e use extensões e modelos profissionais de empresas respeitáveis e mantenha-os atualizados para proteger seu site.

## 9. Atualize a Versão PHP do seu site Joomla

Proteja seu site contra uma variedade de ataques cibernéticos e fortaleça a segurança do seu site Joomla atualizando a versão PHP do seu site para a última versão estável. Certifique-se de selecionar uma versão de PHP que seja compatível com os seus templates e extensões Joomla para evitar problemas no site. Existem várias maneiras de atualizar sua versão PHP. As principais são abordadas em um artigo na edição de setembro de 2020 da Joomla Community Magazine: Como atualizo minha versão do PHP?.

## 10. Reforçar Cabeçalhos de Segurança HTTP

Recomenda-se fortemente implementar ou atualizar cabeçalhos de segurança HTTP, pois eles fornecem uma camada de segurança para o seu site Joomla, ajudando a mitigar ataques e vulnerabilidades de segurança. Normalmente, eles exigem apenas uma pequena alteração de configuração no seu servidor web. Esses cabeçalhos instruem o seu navegador sobre como se comportar ao lidar com o conteúdo do seu site. Abaixo estão seis cabeçalhos de segurança HTTP comuns que devem ser revisados:

- Content-Security Policy
- X-XSS-Protection
- Strict-Transport-Security
- X-Frame-Options
- Public-Key-Pins
- X-Content-Type

## 11. Use uma Extensão de Segurança para Joomla

É necessário limitar as tentativas de login no backend administrativo do Joomla para evitar ataques de força bruta ao seu site Joomla. Isso pode ser implementado por várias extensões de segurança do Joomla que protegem o backend do administrador do seu site contra tentativas de hacking. Você pode encontrar essas extensões na categoria de lista de segurança das Extensões do Joomla.

## 12. Escolha um Provedor de Hospedagem Seguro

Certifique-se de que o provedor de hospedagem que você escolher implemente salvaguardas de segurança para o Joomla. Se optar por uma hospedagem compartilhada, assegure-se de que o subnetting seja implementado levando em consideração a segurança do Joomla. Adquirir um provedor de hospedagem compartilhada barato pode não ser o ponto de partida ideal, pois seu site ficará mais lento, sujeito a spam devido a um "vizinhança ruim" de sites com má reputação, e poderá ser comprometido se outros sites forem hackeados. Além disso, ao escolher um plano de hospedagem, verifique diversos parâmetros como personalização, suporte, avaliações, etc.

## 13. Use SSL para Melhorar a Segurança do Joomla

É altamente recomendável instalar um certificado SSL (Secure Socket Layer) em seu site, pois ele criptografará a comunicação entre seu site Joomla e os navegadores dos visitantes. Adquira um certificado SSL de uma autoridade certificadora verificada e certifique-se de que todo o tráfego HTTP seja redirecionado para HTTPS. Para fazer isso, adicione o seguinte código ao seu arquivo .htaccess:

```
# Redirecionar HTTP para HTTPS
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

## 14. Auditoria de Segurança Frequente no Joomla

É extremamente importante identificar vulnerabilidades antes que um hacker o faça, a fim de manter seu site Joomla seguro e protegido. Isso pode ser feito escolhendo uma ferramenta de auditoria de segurança profissional que possa economizar muito tempo na gestão de seus sites. Auditorias de segurança meticulosas são uma ótima maneira de aprimorar a segurança do seu Joomla. Muitos serviços fazem isso automatizando tarefas, como a criação de backups de sites, a varredura em busca de sinais de intrusão e a atualização em massa das extensões em que você confia. Ele também pode examinar seu site quanto ao uso de melhores práticas de segurança e realizar uma varredura profunda para procurar possíveis ameaças de segurança. Esses serviços utilizam uma combinação otimizada de mecanismos manuais e automatizados para descobrir vulnerabilidades no seu site Joomla.

## 15. Verifique as Mensagens de Pós-instalação

É altamente recomendável ler todas as mensagens de pós-instalação, já que a equipe do Joomla está fornecendo informações importantes que precisam da sua atenção após a atualização ou após instalar o Joomla pela primeira vez. Essas mensagens geralmente contêm configurações de segurança do Joomla ou alterações de arquivos que devem ser feitas manualmente e que uma atualização não pode alterar.

## 16. Conheça as Extensões Vulneráveis

Sempre verifique o site da Lista de Extensões Vulneráveis e suas páginas nas redes sociais para conhecer os riscos de segurança mais recentes e possíveis correções. Recomenda-se desinstalar qualquer extensão listada na Lista de Extensões Vulneráveis para a qual não se conhece uma correção. Certifique-se de atualizar sua extensão vulnerável sempre que sua correção estiver disponível. Se o seu site usa uma versão vulnerável de uma extensão que não possui uma atualização de correção, é recomendável substituí-la.

## Conclusão

Como sempre haverá risco, a segurança do Joomla continuará sendo um processo contínuo, exigindo avaliação frequente dos possíveis vetores de ataque. Os proprietários e administradores de sites devem sempre melhorar a segurança de seus sites para reduzir o risco de comprometimento.

*Traduzido por openai.com*  

