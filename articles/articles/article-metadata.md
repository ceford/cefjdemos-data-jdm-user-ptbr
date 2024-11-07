<!-- Filename: J6.x:_Article_Metadata / Display title: Artigo: Editar - Metadados   -->

## Introdução

Metadados são informações sobre uma página web contidas na primeira parte da página, entre as tags `<head>...</head>`. A maior parte dessas informações não é vista pelos visitantes do site, mas é utilizada por mecanismos de busca para fornecer resultados adequados às solicitações de busca. Portanto, é do seu interesse usar metadados informativos.

Alguns dos itens de metadados são fornecidos pelo modelo em uso e você não precisa configurá-los por conta própria. Exemplos comuns:

```html
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="generator" content="Joomla! - Open Source Content Management">
```
Existem outras formas de metadados, como os dados do Open Graph usados pelo Facebook e os esquemas usados para descrever tipos específicos de página, como Pessoa, Lugar ou Produto. Eles não são abordados aqui.

Os itens de metadados que são frequentemente negligenciados são o **Título** da página, que aparece dentro das tags `<title>...</title>` no `<head>` da página, e a **Descrição** da página, que aparece dentro das tags `<meta>`, mas pode estar ausente. Eles são abordados aqui.

## O Título da Página

Um título de artigo é necessário para qualquer nova página. Algumas diretrizes e dicas para criar bons títulos da Mozilla Developer Network:

>* Evite títulos com uma ou duas palavras. Use uma frase descritiva ou uma combinação de termo-definição para páginas de glossário ou estilo de referência.
>* Motores de busca normalmente exibem cerca dos primeiros 55–60 caracteres de um título de página. Texto além disso pode ser perdido, então tente não ter títulos mais longos que isso. Se precisar usar um título mais longo, certifique-se de que as partes importantes venham antes e que nada crítico esteja na parte do título que pode ser descartada.
>* Não use "amontoados de palavras-chave". Se o seu título for apenas uma lista de palavras, algoritmos frequentemente reduzem a posição da sua página nos resultados de busca.
>* Tente garantir que seus títulos sejam tão únicos quanto possível dentro do seu próprio site. Títulos duplicados—ou quase duplicados—podem contribuir para resultados de busca imprecisos.

Recomendações adicionais do Google:

>- Especifique um título único para cada página.
>- Faça seu título descritivo do conteúdo da página e conciso.
>- Evite o preenchimento de palavras-chave (usar repetidamente palavras similares como "Foobar, foo bar, foobars, foo bars").
>- Evite usar títulos genéricos - cada página deve ter um título único, idealmente atualizado dinamicamente em relação ao conteúdo sendo exibido.
>- Marque seus títulos com a sua marca, mas faça isso de forma concisa e em relação ao conteúdo sendo servido.

Existem várias Ferramentas para Webmasters que podem ser usadas para identificar se há problemas com suas listagens em um mecanismo de busca específico - sempre vale a pena prestar atenção e corrigir quaisquer problemas. Um exemplo:

[Artigo de suporte do Google sobre o uso de títulos para suas páginas da web](http://support.google.com/webmasters/bin/answer.py?hl=en&amp;answer=35624)

No Joomla, para uma única página, o título do artigo se torna o título da página usado na seção head e exibido na aba do navegador. Para uma página composta, como *Artigos em Destaque* ou um *Blog de Categoria*, o Título do item do menu se torna o título da página. Portanto, você precisa pensar na composição de bons títulos descritivos tanto para artigos quanto para itens de menu.

## A Descrição da Página

O artigo *Meta Descrição* é um campo na aba *Publicação* do formulário de entrada de dados do artigo:

![Aba de publicação do formulário de edição do artigo](../../../en/images/articles/articles-edit-publishing-tab.png)

Se não houver uma descrição de metadados do artigo, então uma descrição de metadados de um único item de menu de artigo será usada, se estiver configurada. Se não houver uma descrição de metadados do item de menu, então a descrição meta global do site será utilizada, se estiver configurada. Caso contrário, o campo de descrição de metadados é omitido.

O Google recomenda o seguinte para garantir que você aproveite ao máximo a indexação de seu mecanismo de busca:

>- Garanta que cada página tenha descrições meta únicas e relevantes
>- Garanta que você aplique metadados para páginas de listagem (por exemplo, blog e layouts de lista) além de artigos individuais - isso é comumente negligenciado em sites Joomla!
>- Inclua informações factuais, se relevantes (por exemplo, artigos de blog podem incluir o autor, produtos podem incluir o preço ou fabricante)
>- Considere usar metadados gerados automaticamente - mas certifique-se de que sejam relevantes, legíveis e precisos.
>- Faça suas descrições serem descritivas!

Outra referência:

[Artigo de suporte do Google sobre o uso de metadados](http://support.google.com/webmasters/bin/answer.py?hl=en&amp;answer=35624)

## Palavras-chave

Era uma vez, os motores de busca usavam palavras-chave para ajudar a classificar o conteúdo. Assim, autores enchiam seus metadados de palavras-chave com um grande número delas, na esperança de aumentar seu ranking de SEO. Em resposta, o Google parou de usar palavras-chave para fins de classificação. Pesquise na web por conselhos e você encontrará algumas fontes dizendo para não se preocupar e outras dizendo que elas ainda têm valor.

As palavras-chave não são usadas pelo núcleo do Joomla. Em caso de dúvida, não se preocupe.

## Robôs

O valor padrão de *Usar Global* não insere uma meta tag no cabeçalho da página HTML. Outros valores sim. Há um arquivo `robots.txt` na raiz do site Joomla. Se você deseja controlar os robôs, deve ler este arquivo. Ele contém uma explicação de como usá-lo.

## Autor

Você pode inserir o nome formal do autor para aparecer como metadados.  

## Direitos

Você pode inserir um aviso de direitos autorais para aparecer como metadados.

## Exemplo de metadados

É assim que os metadados aparecem na visualização da fonte do artigo:
Aqui está um exemplo do conteúdo do `<head>` após o preenchimento de todos os campos de metadados:

```html
    <meta charset="utf-8">
    <meta name="rights" content="Charles Darwin © 1859">
    <meta name="author" content="Charles Darwin">
    <meta name="robots" content="noindex, nofollow">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Publicidade para A Origem das Espécies.">
    <meta name="generator" content="Joomla! - Gerenciamento de Conteúdo de Código Aberto">
    <title>Publicidade</title>
```
Note que o campo de saída de palavras-chave está ausente.

*Traduzido por openai.com*

