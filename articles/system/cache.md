<!-- Filename: Cache / Display title: Cache  -->

## Para Administradores

Como administrador, o Joomla oferece a capacidade de armazenar em cache partes do seu site. Você pode optar por armazenar em cache páginas inteiras ou apenas partes dessas páginas. Este guia explica como fazê-lo.

Em uma página da web do site Joomla, há 3 elementos que podem ser armazenados em cache:

1. A página inteira em si – o cache de Página
2. A saída do componente do Joomla para essa página da web – conhecido como cache de Visualização
3. A saída dos módulos exibidos nessa página – conhecido como cache de Módulo

Você tem várias configurações de cache que permitem controlar o que será armazenado em cache:

1. O plugin do sistema "Sistema – Cache de Página"
2. Na Configuração Global, guia Sistema, Configurações de Cache. Aqui, a opção de Cache do Sistema pode ser configurada para
    - DESLIGADO – Cache desativado
    - LIGADO – Cache conservador
    - LIGADO – Cache progressivo
3. Muitos módulos, em suas opções, têm uma guia Avançada na qual o Cache pode ser definido como *Usar global* ou *Sem cache*

Conforme descrito abaixo, também existem regras para cache que são implementadas dentro do código do Joomla e sobre as quais você não tem controle.

Você pode limpar o cache através da seleção de menu Administrador → Sistema → Limpar Cache. Em geral, você pode pensar no Joomla como tendo 3 níveis de cache, aumentando em agressividade:

1. Cache conservador
2. Cache progressivo
3. Cache de página

Além disso, os desenvolvedores do Joomla podem usar facilidades de cache para armazenar o resultado de consultas ao banco de dados, por exemplo, para aumentar a responsividade do site, mas isso está fora do escopo das capacidades do Administrador.

## Cache de Página

Para ativar isso, vá para Administrador → Extensões → Plugins. Em seguida, encontre o plugin System – Page Cache e habilite-o. Isso significa que as páginas do site agora serão armazenadas em cache e, sempre que forem solicitadas novamente, a página em cache será servida, em vez de ser gerada pelo Joomla a partir das informações do banco de dados. A página em cache continuará a ser servida até que expire – conforme definido pelo parâmetro *Tempo de Cache* na aba Administrador → Configuração Global → Sistema → Configurações de Cache.

Se você está lendo esta página como um tutorial e deseja testar o cache de página, é melhor configurar as configurações de cache da Configuração Global para:

- Manipulador de Cache – Arquivo
- Caminho para a Pasta de Cache – deixar em branco
- Tempo de Cache – 15 (o padrão é de 15 minutos)
- Cache Específico para Plataforma - Não
- Cache do Sistema – DESLIGADO – Cache desabilitado

Para verificar se o cache de página está funcionando, vá para uma página do site que exiba um artigo. Após exibir essa página, você deve encontrar no sistema de arquivos um diretório `cache/page` com um arquivo cujo nome é algo como `xxx-cache-page-yyy.php`, onde xxx e yyy são cadeias de caracteres hash longas. O Joomla precisa armazenar páginas de cache separadas para URLs separados, então a segunda sequência de dígitos hexadecimais é um hash do URL da página web do site, para tornar o nome do arquivo exclusivo para essa página.

Em seguida, use a funcionalidade do Administrador para alterar o texto desse artigo e redispense a página web do site. Você deve encontrar a versão em cache, não o seu texto modificado.

Alterar um artigo (ou outro item do Joomla) não limpa o cache de página para a(s) página(s) web onde esse artigo é exibido. Para limpar o cache de página, vá para Administrador → Sistema → Limpar Cache. Clique na caixa de seleção ao lado do *Grupo de Cache* chamado "page" e pressione o botão Excluir. Quando você redispensa sua página web, ela deve agora mostrar o texto alterado.

Se o seu site tiver uma função como um carrinho de compras, aplicar cache de página causará problemas, pois as páginas precisam mostrar o que o cliente já selecionou, em vez de exibir uma página em cache que é comum a todos. No entanto, você pode configurar o plugin System - Page Cache para excluir do cache Itens de Menu específicos ou URLs e intervalos de URLs específicos (na aba Avançado), para que apenas páginas realmente estáticas sejam armazenadas em cache.

## Cache Conservadora

Com o Cache Conservadora, você pode armazenar em cache a saída de visualização de componentes e a saída de módulos que permitem cache. No entanto, observe que isso só funcionará em páginas que não estão sendo armazenadas em cache usando o Cache de Página. Para essas páginas, toda a página web é armazenada em cache, e o Cache Conservadora nem é considerado.

Para ativar o Cache Conservadora:

1. Acesse Administrador → Sistema → Configuração Global → aba Sistema e, dentro das Configurações de Cache, configure Cache do Sistema como ATIVADO – Cache conservadora.
2. Acesse Administrador → Extensões → Módulos e selecione os módulos que você gostaria que fossem armazenados em cache. Se esse módulo permitir cache, então, sob a aba Avançado, você deverá conseguir configurar o Cache para

- Usar Global – este módulo será armazenado em cache (com a opção Global agora configurada para Cache conservadora)
- Sem cache – este módulo não será armazenado em cache.

(Observe que o Tempo de Cache na Configuração Global está em minutos, mas o Tempo de Cache nas configurações de Módulo está em segundos.)

Para verificar se está funcionando, acesse seu site, **certifique-se de que você esteja deslogado**, e navegue até uma página que exiba um artigo. Verifique seu sistema de arquivos e você deve encontrar uma pasta `cache/com_content` contendo um arquivo de cache.

Você também encontrará outros diretórios, como `cache/com_languages` (pois exibir a página envolve carregar o idioma atual, que também será armazenado em cache) e também diretórios relacionados ao cache de módulo, por exemplo, `cache/com_modules`. Estes resultam do uso de cache que os desenvolvedores codificaram dentro da aplicação Joomla.

Se você editar e salvar aquele artigo, depois atualizar a página do site, verá que o site exibirá o texto atualizado dessa vez. Isso ocorre porque toda vez que a edição é salva, o Joomla limpa o cache para aquele artigo.

No entanto, você pode demonstrar que o cache está funcionando se editar o arquivo de cache no diretório `cache/com_content` usando um editor de texto básico. Usando o editor, altere uma letra no texto do artigo no arquivo de cache e salve o arquivo. Então, quando atualizar a página web, verá a alteração que fez no arquivo de cache.

Como você pode selecionar quais visualizações de componente são armazenadas em cache e sob quais circunstâncias? Infelizmente, você não pode fazer isso. Isso é determinado pelos desenvolvedores dos componentes principais do Joomla e codificado no código PHP do componente. Os critérios são diferentes para cada componente. No entanto, você pode facilmente descobrir quais critérios são utilizados, pois para cada um dos componentes do site, eles são codificados no arquivo `DisplayController.php` do site. Por exemplo, no momento desta revisão (versão 5 do Joomla) para o componente Contatos, encontraremos em `components/com_contact/src/Controller/DisplayController.php`

```php
    public function display($cachable = false, $urlparams = [])
    {
        if ($this->app->getUserState('com_contact.contact.data') === null) {
            $cachable = true;
        }
```

Isso significa que as visualizações associadas a contatos serão armazenáveis em cache, a menos que haja dados de sessão com a chave com_contact.contact.data – o que será o caso se na sessão do usuário o usuário tiver exibido um formulário de contato (por exemplo, em uma página apontada por um item de menu do tipo Contatos → Contato Único).

O arquivo equivalente para artigos `components/com_content/src/Controller/DisplayController.php` contém:

```php
    public function display($cachable = false, $urlparams = false)
    {
        $cachable = true;

        /**
         * Configura o nome e formato de visualização padrão a partir da Solicitação.
         * Observe que estamos usando a_id para evitar colisões com o roteador e a página de retorno.
         * O Frontend é um pouco mais bagunçado que o backend.
         */
        $id    = $this->input->getInt('a_id');
        $vName = $this->input->getCmd('view', 'categories');
        $this->input->set('view', $vName);

        $user = $this->app->getIdentity();

        if (
            $user->get('id')
            || ($this->input->getMethod() === 'POST'
            && (($vName === 'category' && $this->input->get('layout') !== 'blog') || $vName === 'archive'))
        ) {
            $cachable = false;
        }
```

A expressão `$user->get('id')` é verdadeira se este for um usuário logado. Isso significa que os artigos nunca são armazenados em cache para usuários logados. As expressões subsequentes se referem a outras condições em que o cache não é realizado, mesmo que o usuário não esteja logado.

Dessa forma, você pode descobrir as circunstâncias sob as quais o armazenamento em cache é realizado, mas alterar isso não é aconselhável. Você também pode demonstrar que os módulos estão sendo armazenados em cache ao usar o módulo de Breadcrumbs do Joomla, garantindo que ele seja exibido em alguma posição de módulo na página da web, configurando sua opção de Cache e editando manualmente o arquivo de cache em cache/mod_breadcrumbs.

## Cache Progressiva

Assim como o Cache Conservadora, o Cache Progressiva também armazena em cache a saída das visualizações dos componentes e dos módulos. A diferença funcional entre os dois é que, com o Cache Progressiva, **para usuários desconectados, todos os módulos estão sempre em cache**. Nesse caso, definir a opção *Sem Cache* para um módulo não tem efeito. Se a opção de armazenamento em cache estiver configurada como *Arquivo*, você pode encontrar o arquivo de cache dos módulos (a saída de todos os módulos é armazenada dentro do mesmo arquivo) no diretório `cache/com_modules`.

Para ativar o Cache Progressiva, vá para Administrador → Sistema → Configuração Global → aba Sistema e, nas *Configurações de Cache*, defina *Cache do Sistema* como *LIGADO – Cache progressiva*.

No que diz respeito às condições para armazenamento em cache das visualizações dos componentes principais do Joomla, **não há diferença entre cache conservadora e progressiva**. Apesar do que você pode ler em alguns sites e respostas a perguntas no Stack Overflow, não é o caso que o Cache Conservadora está relacionado a quando o usuário não está conectado e o Cache Progressiva a quando o usuário está conectado.

## Resumo

Abaixo está um resumo dos tipos de cache.

### Cache de Página Inteira

- **Configuração**: Plugin Embutido (Administrador → Extensões → Gerenciador de Plugins → Sistema - Cache de Página)
- **Cacheia**: cada página inteira do seu site
- **Baseado em**: URL
- **Mais informações**:
  - Cache de navegador opcional: Também armazena no navegador/computador dos seus visitantes
  - Apenas armazena páginas para visitantes não logados (não para visitantes logados). Tenha cuidado ao usar este plugin se você tiver um site interativo onde deseja servir conteúdo baseado em informações de sessão/cookie em vez de apenas na URL simples. Funcionalidades como um carrinho de compras não funcionarão.

### Cache de Visualização

- **Configuração**: Configuração Global -> Cache
- **Cacheia**: cada visualização de um componente
- **Baseado em**: URL, visualização, parâmetros, ...
- **Mais informações**: Os desenvolvedores de componentes precisam incluir isso em seu código para funcionar. Na maioria das vezes, isso não é feito. O principal componente de conteúdo do Joomla usa isso, mas apenas para visitantes não logados do seu site, embora isso não seja obrigatório para todos os componentes.

### Cache de Módulo

- **Configuração**: Configuração Global -> Cache
- **Cacheia**: cada módulo (personalizado individualmente através dos Parâmetros Avançados de cada módulo)
- **Baseado em**: ID do módulo, níveis de visualização do usuário e o parâmetro *Itemid* na requisição HTTP
- **Mais informações**: Você deve desativá-lo em alguns módulos para evitar problemas

### Cache Adicional

Se você deseja explorar outros sistemas de cache e possibilidades, pode querer conferir as extensões de terceiros em torno do cache.

### Motores ou Armazenamentos de Cache

- **Configuração**: Configuração Global -> Cache

Aqui você pode escolher qual sistema deseja que seu site use para todo o cache. Algumas opções são: APC, Eaccelorator, File, Memcache, Redis, XCache.

APC, por exemplo, também armazena em cache o opcode do seu PHP.

## Para Desenvolvedores

<div class="alert alert-warning">
Esta seção precisa de revisão para Joomla! 4/5.
</div>

A classe **JCache** permite vários tipos e níveis de cache. As seguintes subclasses são feitas especificamente, mas você pode adicionar suas próprias, ou usar a principal de muitas maneiras diferentes.

Não se esqueça de que o primeiro nível de cache encontrado, substituirá qualquer cache mais profundo. Suponho que muitos níveis também sejam contraproducentes (*embora isso precise ser verificado*).

- **JCacheView** armazena em cache e retorna a saída de uma determinada visão (em MVC). Um id de cache é gerado automaticamente a partir do URI, visão específica e seu método específico, ou você pode fornecer o seu próprio.

Isso pode ser feito automaticamente através da função de exibição do controlador base. Por exemplo, no controlador do seu componente:

    class DeliciousController extends JController {
        function display() {
            parent::display(true); //true pede por cache.
        }
    }

Há também alguns urlparams a serem considerados. Confira este
[Joomla StackExchange](http://joomla.stackexchange.com/questions/5781/how-can-i-use-joomlas-cache-with-my-components-view/7000#7000 "")

Também esteja ciente de que quaisquer atualizações (como acessos ou contagens de visitas) NÃO serão atualizadas (a menos que você adicione isso fora deste método e, portanto, qualquer parte mais profunda do MVC).

- **JCachePage** armazena em cache e retorna o corpo da página.
- **JCacheCallback** armazena em cache e retorna a saída e os resultados de funções ou métodos.

Se você deseja armazenar consultas em cache, esta é uma boa classe para isso, como ilustrado aqui: Usando cache para acelerar seu código

- **JCacheOutput** armazena em cache e retorna a saída.

Isso é mais direcionado para armazenar em cache uma parte específica do código PHP. Ele atua como um buffer de saída, mas em cache.

*Traduzido por openai.com*

