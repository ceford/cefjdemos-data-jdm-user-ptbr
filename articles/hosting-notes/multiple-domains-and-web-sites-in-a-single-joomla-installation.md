<!-- Filename: Multiple_Domains_and_Web_Sites_in_a_single_Joomla!_installation / Display title: Múltiplos Domínios e Sites em uma única instalação do Joomla! -->

**Nota:** Este artigo foi atualizado pela última vez em 2012!

Embora seja uma boa prática dar a cada site seu próprio domínio, instalação do Joomla! e banco de dados, podem existir condições especiais nas quais uma solução de múltiplos sites em uma única instalação do Joomla! seja justificada.  

## Um Exemplo de Aplicação

Uma pequena empresa, 'Johnson Candies', possui duas marcas separadas mas relacionadas: *Red Candy* e *Yellow Candy*. Eles necessitam de um único site baseado em Joomla! onde ambos os tipos de doces sejam visíveis, cada um com sua própria página inicial no site Joomla!, que corresponde aos domínios `www.redjohnsoncandy.com` e `www.yellowjohnsoncandy.com`.

Além disso, cada marca e site **requerem seu próprio design**: um template amarelo para um; um template vermelho, para o outro.

## Benefícios

Ao incluir ambas as marcas em uma única instalação web do Joomla!, a Johnson Candies consegue economizar tempo de edição (apenas um login), compartilhar artigos e dados entre ambas as marcas (ou sites) e usar um único recurso, como um formulário de Contato, para ambas as marcas.

## Procedimento de Implementação

### Prepare Seus Domínios

Use um único domínio para sua conta de hospedagem, como de costume. Crie os domínios adicionais necessários no painel de controle da sua conta de hospedagem. Para o propósito deste tutorial, usaremos `www.redjohnsoncandy.com` além do domínio base `www.yellowjohnsoncandy.com`.

### Instalar e Configurar o Joomla!

Instale e configure o Joomla! normalmente. Em seguida, desenvolva artigos, menus e módulos para cada site.

### Criar Templates

Desenvolva e instale os templates necessários - um para cada site que você desejar ter. No exemplo acima, você criaria um template para *red candy* chamado *Template Vermelho* e um template para *yellow candy* chamado *Template Amarelo*. Uma vez que os templates estejam instalados, atribua-os aos itens de menu relevantes, usando o gerenciador de templates do Joomla! na área de Administração do Joomla!

### Adicionar um Redirecionamento

#### Opção #1: Criar um redirecionamento .htaccess (Apache)

**Nota** *Habilite URLs SEF no Joomla! Primeiro*

Uma opção é usar .htaccess (Apache) para redirecionar consultas para um determinado domínio para uma página específica do Joomla!

Nosso objetivo é redirecionar quaisquer consultas para o domínio Red Candy para uma página específica no site Joomla! Neste exemplo, redirecionamos quaisquer consultas para `www.redjohnsoncandy.com` para uma página de categoria-blog. Você já teria atribuído o template 'red candy' a este item de menu, para criar a ilusão de um site separado.

```
#A regra a seguir funciona, mas altera o nome do domínio exibido.
RewriteCond %{HTTP_HOST} ^(www\.)?redjohnsoncandy\.com$
RewriteRule (.*) http://www.yellowjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12 [R=301,L]
```
Isso funciona, mas você pode ver a desvantagem imediatamente. Embora o usuário esteja visualizando com sucesso o site Red Candy, ele ainda verá o nome do domínio Yellow Candy. Infelizmente, se você estiver usando ambos .htaccess e estacionamento de domínio (tecnicamente um redirecionamento) - isso é necessário para evitar criar um LOOP.

#### Opção #2: Criar um Redirecionamento de Cabeçalho PHP

Esta solução tem o benefício de manter a ilusão de domínios/sites separados evidente para o visitante. Em vez de usar .htaccess (Apache) para nosso redirecionamento, usamos um dos templates no site.

Neste exemplo, o domínio base é `www.redjohnsoncandy.com`. Você criou um template para essa área chamado *Template Vermelho*. O truque é abrir o arquivo index.php do 'Template Vermelho' e adicionar o seguinte **como as primeiras linhas** do index.php principal da instalação.

```php
<?php
$domain = $_SERVER["HTTP_HOST"];
$uri = $_SERVER["REQUEST_URI"];
$url = $domain . $uri;

if (($url == "redjohnsoncandy.com/") ||
   ($url == "www.redjohnsoncandy.com/")) {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.redjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12");
}
?>
```

Aqui está o benefício: O visitante agora será redirecionado para a página apropriada do *Site Vermelho*, que tem o *Template Vermelho* atribuído **somente** no caso de terem chegado ao nome de domínio do 'site vermelho'. Caso contrário, a regra condicional PHP é ignorada, e o Site Amarelo é carregado.

É importante lembrar de solicitar também a URI (url que segue o domínio puro) para que você possa fazer redirecionamentos para o mesmo domínio. Quando a URI é invisível na url, a variável se torna um sinal "/". Por isso, você deve comparar sua url pura com um sinal "/" no final. Desta forma, você poderá fazer redirecionamentos 301 no mesmo domínio. Caso contrário, você criará um loop infinito no processo de redirecionamento.

#### Opção #3: Criar um Redirecionamento de Cabeçalho PHP, para múltiplos domínios com redirecionamentos específicos de domínio para templates personalizados

Solução para espaço único na web, com diferentes domínios, uma instalação do Joomla e, dependendo do domínio de chegada do usuário, redireciona para uma página padrão diferente. Cole o seguinte código PHP **como a primeira coisa** no arquivo index.php principal da instalação. Para atribuir outro domínio, basta copiar/colar a função "if" e editá-la com os valores do outro domínio da mesma maneira. Além disso, para configurar as visualizações de template, você terá que atribuir diferentes itens de módulo/alias de link e configurar visualizações de template dentro do gerenciador de templates do Joomla! A configuração do alias é necessária quando você usa configurações SEF.

```php
<?php
$domain = $_SERVER["SERVER_NAME"];
$requri = $_SERVER['REQUEST_URI'];
if (($domain == "www.example.de" && $requri == "/" ||
   $domain == "example.de"))  {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.example.de/index.php?option=com_content&view=article&id=6");
}
?>
```

*Traduzido por openai.com*

