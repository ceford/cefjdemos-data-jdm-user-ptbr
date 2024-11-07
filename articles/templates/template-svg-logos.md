<!-- Filename: J4.x:Template_SVG_Logos / Display title: Modelos de Logos SVG -->

## Logotipo Cassiopeia

O modelo de site padrão do Joomla 4, Cassiopeia, usa a palavra CASSIOPEIA como um logotipo de marca. Ele aparece no topo de cada página, a menos que você configure a Marca como Não no formulário Editar Estilo de Modelos, na aba Avançado, ou use uma palavra no Título em vez de um gráfico. Essa palavra é, na verdade, um arquivo gráfico vetorial escalável (SVG). Você pode escolher um gráfico alternativo, mas é bastante complicado criar e usar um logotipo SVG alternativo. Este breve conjunto de instruções pode ajudar.

## Inkscape

Inkscape é um aplicativo de gráficos vetoriais de código aberto e multiplataforma, o que significa que você pode baixá-lo gratuitamente e usá-lo no Linux, Mac ou Windows. Para começar, vá ao site do Inkscape e baixe a versão para o seu laptop ou computador de mesa. Inicie o Inkscape e você estará pronto para criar um Logotipo de Marca em SVG. A imagem abaixo mostra o Inkscape durante a criação de um novo Logotipo SVG.

![criação de logo no inkscape](../../../en/images/templates/templates-svg-logos-inkscape.png)

## Instruções

Para este artigo, é necessário um logotipo que mostre **CASSIOPEIA VERDE** no mesmo tamanho que **CASSIOPEIA** no logotipo padrão, que é de 32 pixels de altura:

1. Inicie o Inkscape, ajuste o tamanho da janela para um tamanho confortável, e selecione Ver / Zoom / Zoom Página.
2. Selecione a Ferramenta Texto, marcada com a letra A na Barra de Ferramentas à esquerda.
3. Selecione Arial, Negrito, 40 e px.
4. Arraste para definir uma caixa ocupando a maior parte da largura da página.
5. Digite o texto: CASSIOPEIA VERDE.
6. Selecione Ver / Zoom Seleção.
7. Selecione a ferramenta Selecionar, marcada por uma seta - na parte superior da Barra de Ferramentas à esquerda.
8. Trave os valores de tamanho Horizontal e Vertical - o símbolo de cadeado na barra superior.
9. Defina a unidade de medida para px.
10. Altere a altura para 32 - você verá o logo mudar para o novo tamanho.
11. Selecione Caminho / Objeto para Caminho - sem mudança visível, mas as palavras deixam de ser texto.
12. Selecione Arquivo / Propriedades do Documento.
13. Selecione Redimensionar para o Conteúdo.
14. Diminua o zoom para uma melhor visualização.
15. Defina o Preenchimento para branco - clique na caixa branca na paleta de cores inferior.
16. Arquivo / Salvar em
    local-site-root/images/headers/green-cassiopeia-optimised.svg
    1. Se você salvar em outro lugar, será necessário usar um gerenciador de arquivos ou FTP para enviar os arquivos SVG. O componente Media pode usar arquivos SVG, mas no momento não faz upload deles.
17. Selecione SVG Otimizado (.svg) na lista de tipos de arquivo na parte inferior da janela de diálogo Salvar.
18. Salve, OK para todas as opções padrão do formulário de saída SVG Otimizado.
19. Defina algumas opções de Administrador do Joomla para permitir o uso de arquivos SVG.
20. Vá para Conteúdo / Mídia / Opções.
    1. Acrescente às extensões permitidas: ,svg
    2. Acrescente às Extensões de Imagem Legais (Tipos de Arquivos): ,svg
    3. Acrescente aos Tipos MIME Legais: ,image/svg+xml
21. Salve e Feche.
22. Vá para Sistema / Modelos de Site / Opções.
    1. Acrescente aos Formatos de Imagem Válidos: ,svg
23. Salve e Feche.
24. Vá para Sistema / Estilos de Modelos de Site.
25. Selecione seu modelo.
26. Na aba Avançado, no campo Logo, use Selecionar para encontrar seu logo recém-criado.
27. Salve e recarregue a página do seu Site.

![resultado criação logotipo inkscape](../../../en/images/templates/templates-svg-logos-inkscape-result.png)

*Traduzido por openai.com*

