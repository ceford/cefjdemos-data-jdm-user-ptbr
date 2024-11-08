<!-- Filename: J4.x:Favicons / Display title: Favicons  -->

## Os Favicons do Joomla!

Favicons são os pequenos ícones que aparecem na aba do navegador ao lado do nome do seu site. Perto do topo do arquivo index.php do template, há três instruções para carregar favicons na página:
```php
    // Navegadores dão suporte a favicons SVG
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon.svg', '', [], true, 1), 'icon', 'rel', ['type' => 'image/svg+xml']);
    $this->addHeadLink(HTMLHelper::_('image', 'favicon.ico', '', [], true, 1), 'alternate icon', 'rel', ['type' => 'image/vnd.microsoft.icon']);
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon-pinned.svg', '', [], true, 1), 'mask-icon', 'rel', ['color' => '#000']);
```
Para o template Cassiopeia, o Joomla buscará os favicons nos seguintes locais:

1.  **media/templates/site/cassiopeia/images** - eles não estão lá, então o Joomla procurará no próximo local.
2.  **media/system/images** - eles estão lá, então o Joomla usará eles a partir daí.

Se você quiser usar seus próprios favicons em vez dos favicons do Joomla, você deve carregá-los no primeiro local: **media/templates/site/cassiopeia/images**. Você pode fazer isso usando o formulário de personalização de Templates. Eles não serão afetados por qualquer atualização do template Cassiopeia.

Favicons às vezes são usados em tamanhos maiores e em locais diferentes da aba do navegador. Por exemplo, esta é uma captura de tela de parte de uma página inicial do Firefox mostrando algumas das localizações favoritas do Usuário:

![exemplos de favicon da página inicial do Firefox](../../../en/images/templates/favicons-firefox-start-collection.png)

Todos os navegadores modernos suportam ícones SVG, então você deve priorizar a criação de um ícone SVG.  

## Sobre SVG

SVG é uma sigla para Scalable Vector Graphics (Gráficos Vetoriais Escaláveis). Um arquivo SVG contém texto em um formato que define as localizações e formas de linhas com cores de linha, cores de preenchimento e assim por diante. A captura de tela a seguir mostra o arquivo *joomla-favicon.svg* aberto em um editor de texto. Os números das linhas são criados pelo editor de texto e não estão presentes no arquivo. As linhas longas representam curvas e estão truncadas aqui para fins de exibição.

![conteúdo do texto do favicon do joomla](../../../en/images/templates/favicons-joomla-favicon-svg-text.png)

Para criar um arquivo SVG, você precisa usar um aplicativo apropriado, como o Inkscape. Aplicativos de gráficos rasterizados como Photoshop ou GIMP não servirão. Se você prefere desenhar um ícone em um aplicativo de gráficos rasterizados, ou se possui um logotipo gráfico rasterizado existente que pode ser adaptado para um ícone, você pode importar o arquivo PNG resultante no Inkscape e rastreá-lo para produzir um arquivo SVG. A imagem rastreada deve ser excluída após o rastreamento!

A criação real de um favicon em SVG está além do escopo deste artigo. A criação de um arquivo padrão *favicon.ico* a partir de um arquivo *joomla-favicon.svg* é muito simples—muitos sites fazem isso online gratuitamente.

## Como Criar Favicons

Se você quer criar seus próprios favicons, a melhor maneira de fazer isso é criando um favicon em SVG e, em seguida, usar uma ferramenta online para gerar todos os outros formatos com esse como entrada. Neste exemplo, é necessário um ícone para atender a um template filho chamado Cassiopeia Green. Um ícone precisa ser quadrado e não muito elaborado, pois o tamanho mínimo de exibição é 16x16 pixels. Alguns dispositivos precisam de resoluções mais altas, como 32x32 ou 180x180, e o Google recomenda múltiplos de 48x48 pixels. Se você começar com um SVG, não precisa se preocupar com nada disso - basta criar uma imagem quase quadrada com um design adequado. Neste exemplo, o favicon será as letras *J4* em verde escuro.

### Inkscape

O Inkscape é uma aplicação gratuita, open source, multiplataforma, para gráficos vetoriais, usada para trabalhar com arquivos SVG. Funciona em Linux, Mac e Windows. Acesse o site do Inkscape (inkscape.org) para baixar uma cópia para sua plataforma. As ilustrações a seguir mostram a tela do Inkscape em meio às instruções abaixo.

![inkscape com favicon em preparação](../../../en/images/templates/favicons-inkscape-favicon.png)

### Criar um SVG

1.  Inicie o Inkscape e faça a janela ficar em um tamanho confortável: selecione Visualizar / Zoom / Zoom Página
2.  Selecione a Ferramenta de Texto, marcada com a letra A na Barra de Ferramentas à esquerda
3.  Selecione Arial, Normal, 48 e px
4.  Arraste para definir a caixa em qualquer lugar da página
5.  Digite o texto: J4
6.  Selecione Visualizar / Seleção de Zoom
7.  Selecione Caminho / Objeto para Caminho - não há mudança visível, mas as palavras não são mais texto
8.  Selecione Arquivo / Propriedades do Documento
9.  Selecione Redimensionar para Conteúdo
10. Diminua o zoom para uma visão melhor - mas certifique-se de que todas as letras ainda estão selecionadas
11. Defina a caixa de altura com o mesmo valor da caixa de largura. Digite!
12. Feche a caixa de diálogo Propriedades do Documento
13. Visualizar / Zoom Página novamente - os caracteres precisam ser centralizados
14. Editar / Selecionar Tudo
15. Objetos / Alinhar e Distribuir
16. Mover seleção como grupo / Relativo à Página / Centralizar no eixo horizontal - você deve ver o J4 movendo-se para o ponto médio vertical
17. Selecione o Preenchimento e o Traço à direita - o painel à direita possui uma lista suspensa marcada com uma seta para baixo
18. No painel de Preenchimento e Traço, selecione Preenchimento e o primeiro quadrado preenchido
19. No painel RGB, insira 006400ff no campo RGBA próximo ao canto inferior direito - o código para o estilo CSS *darkgreen*
20. Arquivo / Salvar
21. Na caixa de diálogo Salvar, insira um nome de arquivo adequado, por exemplo, green-favicon-j4.svg
22. Selecione um local adequado, por exemplo, *~/Documents/joomla-dev/svgs*
23. Selecione SVG Otimizado (*.svg*) na lista suspensa na parte inferior do formulário.
24. Selecione *Salvar*
25. Selecione *OK* para todos os Padrões no formulário de Saída de SVG Otimizado
26. Feche o SVG no qual você está trabalhando - há uma oportunidade de salvar a imagem no formato Inkscape, mas você realmente não precisa fazer isso.

### Editar o SVG com um Editor de Texto

Inicie seu editor de texto favorito para fazer algumas alterações que não eram possíveis no Inkscape.

1.  Abra seu arquivo SVG recém-criado - note que a primeira linha é uma especificação XML
2.  Você pode excluir a segunda linha - um comentário contendo Criado com Inkscape
3.  Se estiver presente, você pode excluir a linha contendo texto, pois não há texto
4.  Abra o arquivo joomla-favicon.svg original - está em *joomla_root/media/system/images*
5.  Copie o bloco de estilo e cole no seu SVG na linha seguinte à declaração SVG
6.  Feche o arquivo *joomla-favicon-svg* original para evitar alterações acidentais nele
7.  No bloco de estilo do seu próprio arquivo SVG altere caminho {fill: \#000;} para caminho {fill: \#006400;}, o valor na linha
8.  Remova *fill="#006400"* da linha
9.  Salve
10. Abra a imagem no seu navegador. Para o Firefox isso é Arquivo / Abrir Arquivo...

Você deve ver a imagem no seu navegador. O exemplo mostra J4 com 47 pixels quadrados. A próxima etapa é criar os outros tipos de ícones que você precisa usando seu SVG recém-criado como mestre.

### Processamento Online

Acesse o site do Real Favicon Generator. Outros sites estão disponíveis, mas este parece particularmente abrangente.

1.  Selecione o botão rotulado *Select your Favicon image*
2.  O site mostrará sua Imagem Mestre. Diz também *Your picture is not square (688x512). We can fix this by adding transparent margins*
3.  Selecione o botão *Continue with this picture* abaixo da Imagem Mestre.
4.  Há sub-formulários com fundos azul claro para vários tipos de ícones - preencha cada um verificando se a visualização lhe convém.
5.  É melhor ficar com os padrões das Opções do Gerador de Favicon, a menos que você saiba melhor. Exceto:
6.  Caminho, selecione a opção I cannot ... e insira: *media/templates/site/cassiopeia-green/images*
7.  Selecione o botão *Generate your Favicons and HTML Code*
8.  Após um curto atraso, há um novo formulário, selecione o botão Download your package: *Favicon* package
9.  Salve o download ...
10. Selecione e copie o bloco de links para salvar em algum lugar.
11. Feche o site de processamento online

O download é um arquivo *zip* contendo 10 itens: *favicon.ico*, *safari-pinned-tab.svg*, seis arquivos PNG, *browserconfig.xml* e *site.webmanifest*.

### Implantação

Para usar o conjunto padrão de favicons do Joomla, você precisa renomear e mover os ícones para *joomla_root/media/templates/suamodelo/images*:

- Sua imagem SVG mestre, *green-favicon-j4.svg*, deve ser renomeada para *joomla-favicon.svg*
- O arquivo baixado *safari-pinned-tab.svg* precisa ser renomeado para *joomla-favicon-pinned.svg*
- O arquivo baixado *favicon.ico* apenas precisa ser movido

### O Bloco de Links

O bloco de links copiado anteriormente contém:

```html
<link rel="apple-touch-icon" sizes="180x180" href="media/templates/site/cassiopeia-green/images/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="media/templates/site/cassiopeia-green/images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="media/templates/site/cassiopeia-green/images/favicon-16x16.png">
<link rel="manifest" href="media/templates/site/cassiopeia-green/images/site.webmanifest">
<link rel="mask-icon" href="media/templates/site/cassiopeia-green/images/safari-pinned-tab.svg" color="#5bbad5">
<link rel="shortcut icon" href="media/templates/site/cassiopeia-green/images/favicon.ico">
<meta name="msapplication-TileColor" content="#ffc40d">
<meta name="msapplication-config" content="media/templates/site/cassiopeia-green/images/browserconfig.xml">
<meta name="theme-color" content="#ffffff">
```

Provavelmente você não precisa usá-lo!

*Traduzido por openai.com*

