<!--
{
    "source": "https://docs.joomla.org/J4.x:Setting_Up_Your_Local_Environment",
    "title": "Configura\u00e7\u00e3o do Ambiente Local",
    "description": " ",
    "author": ""
}
-->

Desde o Joomla! 4, alteramos o processo de desenvolvimento. Não é mais
possível clonar o repositório e ter uma instalação utilizável do Joomla.
Seguimos as melhores práticas e implementamos um processo de compilação para o CMS.

## Guia de Início Rápido

As etapas para configurar seu ambiente de desenvolvimento dependem do seu
sistema operacional. Não podemos escrever documentação para todos os sistemas
operacionais (SO); use seu mecanismo de busca favorito para encontrar um
tutorial.

### Ferramentas Necessárias

1.  PHP — basicamente o mesmo que você precisa para executar um site Joomla, mas
    é necessária a versão CLI do PHP (interface de linha de comando). (Consulte
    a página [Configurando um servidor LAMPP para desenvolvimento em PHP](https://docs.joomla.org/Special:MyLanguage/Configuring_a_LAMPP_server_for_PHP_development "Special:MyLanguage/Configuring a LAMPP server for PHP development").)
2.  Composer — para gerenciar as dependências PHP do Joomla. Para obter ajuda
    na instalação do Composer, leia a documentação
    em <a href="https://getcomposer.org/doc/00-intro.md" class="external free"
    target="_blank"
    rel="nofollow noreferrer noopener">https://getcomposer.org/doc/00-intro.md</a>.
3.  Node.js — para compilar os arquivos JavaScript e SASS do Joomla. Para obter ajuda
    na instalação do Node.js, siga as instruções disponíveis
    em <a href="https://nodejs.org/en/" class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://nodejs.org/en/</a>. Observação:
    você precisará do NodeJS 12 ou superior para instalar o Joomla.
4.  Git — para gerenciamento de versões.

### Etapas para Configurar o Ambiente Local

1.  Clone o repositório
2.  Faça checkout do branch da versão mais recente.
3.  Execute `composer install` (composer = gerenciador de pacotes para PHP) a partir da
    raiz do repositório git. (Você pode adicionar *--ignore-platform-reqs* se
    não tiver o PHP-LDAP instalado localmente e não precisar dele.)
4.  Execute `npm ci` (npm = gerenciador de pacotes para JavaScript, o parâmetro
    "ci" significa "instalação limpa") a partir da raiz do repositório git.
    (Observação: você precisa do npm 10.1.0 ou superior para isso.
    Execute `npm install -g npm@lts` para atualizar sua versão do npm para a
    versão LTS.)

Usuários de Linux e OSX podem configurar o seguinte alias do bash colocando o
seguinte dentro do *arquivo ~/.bashrc*:

```
    alias jclean="rm -rf administrator/templates/atum/css; \
    rm -rf templates/cassiopeia/css; \
    rm -rf administrator/templates/system/css; \
    rm -rf templates/system/css; \
    rm -rf media/; \
    rm -rf node_modules/; \
    rm -rf libraries/vendor/; \
    rm -f administrator/cache/autoload_psr4.php; \
    rm -rf installation/template/css"
    alias jinstall="jclean; composer install; npm ci"
```

Isso excluirá todos os arquivos compilados do seu sistema e executará uma
nova instalação como um único comando, chamando `jinstall` dentro da sua
instalação do Joomla.

## Um Guia de Início um Pouco Mais Longo

O Joomla é semelhante a muitas outras ferramentas web atualmente. Ele tem uma grande parte
em PHP e possui cada vez mais código JavaScript. Embora a programação em PHP não
precise de tanta preparação, o JavaScript requer muitas ferramentas auxiliares. O
principal motivo é que ninguém escreve código de uma forma que todos os navegadores
entendam, portanto o código precisa ser transpilado, por exemplo, de ES6 para uma
versão compatível do JavaScript. O mesmo vale para CSS. No Joomla, usamos
SASS, que será convertido para CSS nativo para que qualquer navegador
o entenda. Por outro lado, configurar um ambiente de desenvolvimento é
um pouco mais complicado, mas as ferramentas tornam a programação mais conveniente.
Graças aos observadores e ao recarregamento automático do navegador, você pode ver
suas alterações em tempo real.

### PHP

Deve ser suficiente executar `composer install`, pois isso instalará as dependências PHP
salvas no arquivo *composer.lock*. Você pode fazer isso quantas vezes quiser. Ele
instalará apenas novos pacotes quando o arquivo *composer.lock* for alterado.
Não execute `composer update`, pois isso atualizará todos os pacotes para versões mais
recentes e atualizará o arquivo *composer.lock*.

**Observação:** talvez seja necessário executar `composer install` com
a opção `--ignore-platform-reqs` para ignorar os requisitos da plataforma
especificados no Composer. Ou seja, se você não tiver a extensão LDAP do PHP
instalada.

### Scripts do Node/npm

O Node.js vem com um gerenciador de pacotes chamado NPM (em alguns aspectos, semelhante
ao Composer). O NPM possui um comando `run`, e preparamos alguns scripts
para facilitar sua vida. Você deve executar os comandos na raiz do repositório quando
tiver alterado arquivos JS ou SASS. Antes, era necessário executar `npm ci` uma vez
para instalar as dependências.

#### npm run build:css (até o Joomla 6.1)

Ele compilará os arquivos SASS para CSS e também criará os arquivos minificados.

#### npm run build:js (até o Joomla 6.1)

Ele compilará e transpilará os arquivos JavaScript para o formato correto
e criará arquivos minificados.

#### A partir do Joomla 6.2, use os seguintes comandos:

- npm run build -- -n <extension> para recompilar uma extensão específica
- execute npm run builders-list para encontrar o nome da extensão
- npm run build -- --all para recompilar tudo

## Possíveis problemas

Ao executar `composer install`, você pode encontrar estes erros

```
    Problem 1
        - Installation request for joomla/ldap 2.0.0-beta -> satisfiable by joomla/ldap[2.0.0-beta].
        - joomla/ldap 2.0.0-beta requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
    Problem 2
        - Installation request for symfony/ldap v5.1.5 -> satisfiable by symfony/ldap[v5.1.5].
        - symfony/ldap v5.1.5 requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
```

A solução é executar `composer install` com a opção
`--ignore-platform-reqs` para ignorar os requisitos de plataforma
especificados no Composer. Ou seja, se você não tiver a extensão LDAP
do PHP instalada.

```
    composer install --ignore-platform-reqs
```

Se você receber um erro de login como o mostrado abaixo, exclua
o arquivo `administrator/cache/autoload_psr4.php`.

![tela de erro de login do Joomla 4](../../../en/images/hosting-local/local-environment-setup/01-joomla-4-login-error-screen.png)

*Traduzido por openai.com*