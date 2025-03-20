<!-- Filename: Localhost / Display title: Schema.org - Customizado -->

## Propósito

O plugin de esquema personalizado é usado para inserir informações personalizadas no formato JSON-LD bruto. Não é um tipo de Schema Org.

Abra um formulário de edição de artigo e selecione a aba Esquema para escolher um tipo de Esquema e definir os dados para esse tipo. Se um tipo de Esquema não estiver presente na lista, seu Plugin pode estar desativado. Os valores a serem inseridos em cada campo são, em sua maioria, autoevidentes.

Este é um exemplo de um rich snippet artesanal:

```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "Your Article Title",
  "description": "A brief description of the article.",
  "timeRequired": "PT5M"
}
```

A propriedade *timeRequired* representa o tempo estimado de leitura no formato de duração ISO 8601. Neste caso, PT5M significa *5 minutos*.

## Exemplo de Captura de Tela

Abaixo está um exemplo de um campo de esquema personalizado em um formulário de edição de artigo.

![A custom schema edit form](../../../en/images/schemas/edit-schema-custom.png)

*Traduzido por openai.com*

