<!-- Filename: Installing_an_extension / Display title: Instalando uma extensão -->

## Documentação da Extensão

Antes de começar, é sempre sensato ler a documentação associada a uma extensão. A maioria das extensões possui páginas iniciais e fóruns, e é uma boa ideia consultá-los primeiro. Se houver um arquivo README incluído com a extensão, você deve lê-lo. Pode haver instruções especiais de instalação ou configuração.

## Sistema Instalar Extensões

O formulário Sistema / Instalar / Extensões está bem documentado na tela de Ajuda. O que não é tão óbvio é que cada um dos métodos de instalação é um plugin. Nas primeiras edições do Joomla 4, o plugin Instalar da Web era o primeiro na lista, e é possível que ainda seja o caso em versões que foram atualizadas. Ter esse método primeiro é inconveniente se você geralmente usa um dos outros métodos, porque demora alguns segundos para buscar dados do site do Diretório de Extensões Joomla.

Para alterar a ordem:

- Vá para **Painel Inicial / Plugins**.
- Selecione **instalador** no filtro suspenso **Selecionar Tipo**.
- Selecione o ícone **Ordem de Classificação** para revelar os manipuladores de classificação (reticências verticais).
- Arraste o item **Instalador - Instalar da Web** para o final da lista.
- Volte para **Sistema / Instalar / Extensões** para ver o resultado.

Você então estará pronto para usar um dos métodos padrão de instalação.

### Carregar Arquivo de Pacote

Para a maioria das extensões e usuários, o procedimento será:

- Baixar a extensão para sua máquina local como um arquivo zip.
- No backend do seu site Joomla (administração), selecione **Sistema → Instalar → Extensões**.
- Na aba **Carregar Arquivo de Pacote**, selecione o botão *Procurar arquivo* e escolha o pacote da extensão no seu computador local ou arraste e solte o arquivo do seu gerenciador de arquivos.
- O processo de upload e instalação começa automaticamente.
- Algumas extensões podem fornecer instruções adicionais para instalação.
- Note que módulos e plugins geralmente precisam ser habilitados antes de funcionarem.

### Instalar a partir da Pasta

Algumas extensões podem ser grandes demais para usar o método Carregar Arquivo de Pacote, normalmente por um limite no *Tamanho Máximo de Upload de Arquivo* definido pelo seu host. Nesse caso, você pode usar o método Instalar a partir da Pasta.

- Crie um diretório temporário no seu disco rígido local e descompacte o arquivo de arquivo da extensão nesse diretório temporário.
- Usando FTP, carregue o conteúdo deste diretório (incluindo arquivos e subdiretórios) para o diretório /tmp na raiz do Joomla no seu servidor, de modo que você tenha um caminho como /tmp/acmeextension.
- No campo Diretório de Instalação, especifique o diretório do servidor onde você carregou os arquivos e subdiretórios do pacote, por exemplo, /home/username/public_html/tmp/acmeextension.
- Selecione o botão **Verificar e Instalar** e o Joomla! instalará o conteúdo do diretório fornecido.

### Instalar a partir da URL

Em vez de baixar um arquivo zip para o seu computador local, você pode usar apenas a URL de download. O Joomla buscará o arquivo zip diretamente, economizando as etapas de download e upload dos métodos anteriores.

### Instalar da Web

Esta opção permite instalar uma extensão diretamente do Diretório de Extensões do Joomla! A lista inicial está em ordem do número de avaliações, mas você pode selecionar por Categoria para encontrar rapidamente uma lista de extensões que possam atender às suas necessidades.

## Descoberta de Instalação do Sistema

Conforme descrito na tela de Ajuda, a função Descoberta permite que você instale extensões que são grandes demais para alguns sistemas, especialmente ambientes de hospedagem compartilhada de baixo custo. Algo que pode não ser óbvio é que você pode precisar criar pastas em diferentes locais no seu serviço de hospedagem, tipicamente:

- Carregar arquivos do site para siteroot/components/com_mybigcomponent
- Carregar arquivos do administrador para siteroot/administrator/components/com_mybigcomponent
- Carregar mídia (css e javascript) para siteroot/media/com_mybigcomponent
- Carregar arquivos de idioma do site para siteroot/language/en-GB se eles não estiverem em uma pasta de idioma na pasta do site do componente.
- Carregar arquivos de idioma do administrador para siteroot/administrator/language/en-GB se eles não estiverem em uma pasta de idioma na pasta do administrador do componente.

Com isso feito, a Descoberta deverá encontrar e permitir a instalação do componente e poderá realmente funcionar.

## Idiomas de Instalação do Sistema

O idioma padrão é o inglês GB. Ele não pode ser removido ou instalado. Pode não ser óbvio, mas todas as páginas carregam primeiro as strings en-GB apropriadas para garantir que as chaves de idioma usadas pelos programadores não apareçam na saída da página. Se o idioma selecionado pelo usuário não for o inglês, então o idioma do usuário é carregado, sobrescrevendo as strings em inglês. Se um idioma não for totalmente traduzido, o resultado será uma mistura do idioma do usuário e de strings em inglês. Isso pode parecer estranho, mas é melhor do que uma mistura do idioma do usuário e das chaves dos programadores.

Na lista de idiomas disponíveis, selecione o que precisar instalar. Alguns estão marcados com um botão verde para indicar que estão atualizados com a versão atual do Joomla. Outros estão marcados com um botão amarelo para indicar que não estão completamente atualizados. Vá em frente e instale de qualquer forma. Você pode ver algumas palavras em inglês em lugares que deveriam estar no idioma selecionado. Mas isso pode ser raro.

*Traduzido por openai.com*

