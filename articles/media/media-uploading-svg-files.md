<!-- Filename: J4.x:Media:_Uploading_SVG_files / Display title: Fazendo upload de arquivos SVG -->

## Introdução

Arquivos SVG (Gráficos Vetoriais Escaláveis) não são suportados no Joomla por padrão. Algumas etapas são necessárias para permitir que o componente de Mídia os suporte.

## Opções de Mídia

No menu do Administrador:

* Selecione **Mídia** no *Painel Inicial* ou no menu de *Conteúdo*.
* Selecione o botão **Opções** na *Barra de Ferramentas* da Mídia.

Existem 3 campos a serem atualizados, todos são listas separadas por vírgulas, portanto, você só precisa adicionar uma vírgula e o valor apropriado:

- Em *Extensões Permitidas*, adicione ao final da lista já disponível: `,svg`.
- Em *Extensões de Imagem Legais*, adicione ao final da lista já disponível: `,svg`.
- Em *Tipos de MIME Legais*, adicione ao final da lista já disponível: `,image/svg+xml`.
- **Salvar & Fechar**

A partir de agora, você deve ser capaz de fazer upload de arquivos SVG no Gerenciador de Mídia. A menos que...

## O Joomla ainda impede o upload de arquivos SVG?

SVG não é um formato de imagem rasterizada (como arquivos PNG, que contêm pixels), é escrito em XML (Linguagem de Marcação Extensível). É baseado em texto, utilizável diretamente dentro do DOM (Modelo de Objeto de Documento), o CSS pode alterar propriedades e o JavaScript pode adicionar interatividade.

Como tal, arquivos SVG são suscetíveis a todos os padrões de ataque relacionados ao XML:

- Cross-site scripting – ou XSS (através de sua tag `<script>` e eventos).
- Injeções de HTML (através do elemento `<foreignObject>` – foreignObject permite que você inclua elementos de um namespace XML diferente).
- Negação de serviço (se o elemento `<xlink:href>` for mal utilizado).

A partir do Joomla 4.1, uma ferramenta de saneamento é usada para verificar o conteúdo de qualquer arquivo SVG enviado através do Gerenciador de Mídia. As regras são rigorosas e garantem que os arquivos não possam prejudicar o site. Portanto, alguns arquivos podem precisar ser **limpos** manualmente (lembre-se, arquivos SVG são arquivos de texto e podem ser editados em um editor de texto) ou através de uma ferramenta externa antes que possam ser enviados com sucesso.

**Dica:** esses sites irão limpar arquivos SVG criados no *Inkscape*:

* [Teste de Sanitização de SVG](https://svg.enshrined.co.uk/)
* [Limpeza & Otimização de SVG](https://iconly.io/tools/svg-cleaner)
* [SVGminify.com](https://www.svgminify.com/)

*Traduzido por openai.com*

