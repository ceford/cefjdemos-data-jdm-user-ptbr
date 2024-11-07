<!-- Filename: Adding_an_image_to_an_article / Display title: Artigo: Editar - Imagens -->

## Introdução

É importante entender que as imagens para documentos web são armazenadas separadamente do texto HTML. Quando uma página web é solicitada, o navegador primeiro busca o texto e arquivos de suporte separados, como folhas de estilo e scripts JavaScript. As imagens são buscadas posteriormente. Frequentemente, o navegador e o servidor web negociam qual versão de uma imagem buscar para se adequar ao tamanho e à resolução da tela do navegador. Existe até uma extensão do Joomla disponível que cria várias versões de uma imagem principal em diferentes tamanhos e formatos para melhorar a velocidade de entrega e renderização.

As imagens são incorporadas nas páginas web pela inclusão de links devidamente formatados. Existem dois mecanismos diferentes para incluir imagens em artigos:

- A guia *Conteúdo* do formulário de edição permite a inserção de um ou mais links de imagem diretamente no texto do artigo. Este é o tema deste artigo.
- A guia *Imagens e Links* do formulário de edição permite a inclusão de uma imagem como uma *Imagem de Introdução* ou uma *Imagem Completa do Artigo*, ou ambas. Isso é abordado em um artigo separado sobre [Imagens e Links](jdocmanual?article=user/articles/article-images-and-links).

Vale a pena fazer uma distinção entre imagens locais e imagens remotas:

- **Imagens Locais** estão localizadas no mesmo site da instalação do Joomla, geralmente na pasta *imagens*. Os links das imagens não precisam incluir o protocolo e o nome do domínio, pois são obtidos das configurações do site.
- **Imagens Remotas** estão localizadas em outro lugar na internet. Elas precisam incluir o protocolo e o nome do domínio no link. O uso de imagens remotas por meio de tal *hot-linking* pode ser permitido hoje, mas não amanhã. O uso de imagens remotas sem permissão é considerado má etiqueta ou até mesmo roubo.

## Adicionando uma imagem local

A melhor maneira de inserir imagens locais é utilizando o botão **CMS Conteúdo → Mídia** na barra de ferramentas de edição do TinyMCE. Ele abre um diálogo de Mídia que permite a seleção de qualquer imagem na pasta de imagens do site.

**Importante:** Primeiro, posicione o cursor onde você deseja que a imagem apareça. Isso pode ser no início ou no final de um parágrafo ou em um parágrafo vazio.

![O diálogo de popup de mídia](../../../en/images/articles/articles-edit-images-media.png)

No diálogo de popup, navegue até a imagem que você deseja usar e selecione-a. Ao selecionar, um formulário aparecerá solicitando dados adicionais.

- **Descrição da Imagem (Texto Alternativo)** Isso é importante para fins de acessibilidade e conformidade com os padrões da web.
- **Classe da Imagem** Se uma imagem for usada sem legenda, algumas classes personalizadas podem ser aplicadas aqui. Por exemplo, *float-end ms-2 mb-1* alinhará a imagem à direita e o texto flutuará ao redor com margens à esquerda e abaixo para evitar que o texto toque na imagem.
- **Classe da Figura** Se uma legenda estiver definida, então uma classe de alinhamento, se houver, pode ser aplicada à Figura. Note que no Cassiopeia as margens são aplicadas à figura pela folha de estilo do template, então *float-start* ou *float-end* são suficientes.
- **Legenda da Figura** Habilita a legenda que exibe o conteúdo deste campo como uma legenda abaixo da imagem.

**Importante:** Se o campo *Legenda da Figura* estiver vazio, a imagem será inserida dentro de uma tag `<img...>` e o campo *Classe da Figura* não será usado. Se o campo *Legenda da Figura* contiver texto, a tag `<img...>` será envolvida em tags `<figure>...</figure>`. As classes mais úteis para adicionar são *float-start* e *float-end* para posicionar a imagem à esquerda ou à direita da página, com o texto fluindo ao redor.

Selecione o botão *Inserir Mídia* para inserir a imagem. A tela de Inserir Imagem se fechará e a imagem será exibida no editor. Ou selecione o botão *Cancelar* para sair da tela de Inserir Imagem.

**Dica:** selecione o botão Alternar Editor para ver os estilos de Imagem e Figura aplicados. Pode ser necessário cortar e colar uma figura ou img para movê-la.

### Usando Arrastar e Soltar para Imagens Locais

Você pode arrastar uma imagem da área de trabalho ou de um navegador de arquivos diretamente para o texto do artigo e a imagem será carregada na pasta de mídia e colocada no artigo. A única ressalva é que todas essas imagens carregadas serão colocadas na mesma pasta de mídia.

A localização do *Diretório de Imagens* usado para upload e se esse recurso está habilitado (ativado por padrão) são configurados nas Opções de configuração do TinyMCE.

## Adicionando um link de imagem remota

Se a imagem que você deseja usar não estiver na pasta de imagens da sua instalação do Joomla, é necessário um procedimento ligeiramente diferente.

- Selecione **Inserir → Imagem** na barra de ferramentas do TinyMCE para abrir uma caixa de diálogo.
- No campo **Fonte**, insira a URL da imagem.
- Preencha os outros campos conforme necessário.
- A aba **Avançado** oferece algumas opções de formatação aplicadas como estilos em linha. Experimente com 1rem, 2, groove.

![A caixa de diálogo de inserção de imagem](../../../en/images/articles/articles-edit-images-external-image.png)

### Usando Arrastar e Soltar para inserir links de imagem remota

Você pode arrastar e soltar um link de imagem de um site remoto diretamente no texto do seu artigo. Mas esteja ciente de que isso também pode copiar o HTML do contêiner da imagem com declarações de classe que não são válidas para o seu site.

## Enviando imagens usando o diálogo de Mídia

Você pode enviar novas imagens para a sua pasta de imagens a partir da página 
*Conteúdo do CMS -> Mídia*.

- Abra o diálogo de Mídia e navegue até a pasta onde você deseja armazenar novas imagens para o artigo atual.
- Selecione o botão Upload no canto superior esquerdo da tela de Mídia para abrir um navegador de arquivos.
- Selecione os arquivos de imagem que deseja enviar. Selecione Abrir no navegador de arquivos para confirmar a seleção. Nota: O estilo e layout do navegador de arquivos dependem do navegador e sistema operacional que você está usando.
- O(s) arquivo(s) selecionado(s) aparecerão em ordem alfabética na tela de Mídia/Imagem.
- Quando o envio estiver completo, uma confirmação verde aparecerá no topo da tela.

Agora você pode selecionar e inserir a imagem enviada como antes.

*Traduzido por openai.com*

