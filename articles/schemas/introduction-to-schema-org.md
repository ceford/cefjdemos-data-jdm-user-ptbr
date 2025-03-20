<!-- Filename: J5.x:Schema_org / Display title: Introdução aos Esquemas -->

## Rich Snippets

Rich snippets (também conhecidos como *rich results*) são resultados normais de pesquisa do Google com dados adicionais exibidos. Esses dados extras são geralmente compilados a partir de dados estruturados encontrados no HTML de uma página. Tipos comuns de rich snippets incluem avaliações, receitas e eventos. Rich snippets podem ajudar sites a se destacarem nos resultados de busca, atrair mais cliques e fornecer aos usuários uma melhor compreensão do conteúdo antes de clicarem.

Joomla implementa Rich Snippets usando JSON-LD. Esta é uma notação JavaScript embutida em uma tag `<script>` no elemento `<head>` de uma página HTML. A marcação não é intercalada com o texto visível pelo usuário. O conteúdo dos snippets é inserido em campos de formulário implementados com plugins.

## Schema.org

>Schema.org é uma atividade colaborativa da comunidade com a missão de criar, manter e promover esquemas para dados estruturados na Internet, em páginas da web, em mensagens de e-mail e além.

Dados estruturados são um formato padronizado para organizar e representar informações na web. Ele fornece uma maneira de descrever o conteúdo e o significado dos dados de forma estruturada, facilitando a compreensão e o processamento das informações por mecanismos de busca e outras aplicações. Há mais informações detalhadas no [site do Schema.org](https://schema.org/).

## Implementação do Joomla

No Joomla, os Rich Snippets são gerados usando a marcação de dados estruturados com base nos esquemas do Schema.org. Cada tipo de esquema é implementado como um plugin separado. Isso permite uma arquitetura mais modular e extensível. Cada plugin é responsável por gerar a marcação de esquema para um tipo específico de conteúdo, o que permite mais flexibilidade e opções de personalização. Isso facilita a contribuição de desenvolvedores terceiros para o desenvolvimento das capacidades de dados estruturados do Joomla.

Para começar, vá para **Sistema -> Plugins** e ative o plugin *System - Schema.org*. Se esse plugin não estiver ativado, não haverá uma aba Schema em um formulário de edição de artigo, mesmo que todos os plugins individuais estejam ativados.

![List of schema plugins](../../../en/images/schemas/schema-plugins-list.png)

### Editar Sistema - Plugin Schema.org

- **Tipo Base** Escolha se o seu site representa uma organização ou uma única pessoa.
- **Nome** Insira o nome da organização ou pessoa que o site representa.
- **Imagem** Adicione a imagem da sua empresa ou pessoal
- **Contas de Mídia Social** Adicione as contas de mídia social da sua empresa ou pessoal. Selecione o botão verde de mais para adicionar linhas ao formulário.
- Selecione **Salvar e Fechar**.

![edit system schema org plugin](../../../en/images/schemas/edit-system-schema-org-plugin.png)

### Editar um Artigo

Vá para qualquer um dos seus artigos e preencha os campos do formulário de Esquema. Se o *Tipo de Esquema* estiver definido como *Nenhum*, o padrão, não há campos a serem preenchidos. Selecione qualquer Esquema para ver uma lista de campos apropriados para esse esquema. A captura de tela a seguir mostra um artigo com o esquema de Artigo selecionado:

![edit article scheme form](../../../en/images/schemas/schema-form-in-an-article.png)

### Saída

Você não verá nada relacionado ao esquema na página da web. No entanto, se você olhar o código-fonte da página, verá uma entrada de script, como no exemplo a seguir:

```json
	<script type="application/ld+json">{
    "@context": "https://schema.org",
    "@graph": [
        {
            "@type": "Organization",
            "@id": "http://localhost/jcms-testing/#/schema/Organization/base",
            "name": "Joomla Documentation Team",
            "url": "http://localhost/jcms-testing/"
        },
        {
            "@type": "WebSite",
            "@id": "http://localhost/jcms-testing/#/schema/WebSite/base",
            "url": "http://localhost/jcms-testing/",
            "name": "JCMS Testing",
            "publisher": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            }
        },
        {
            "@type": "WebPage",
            "@id": "http://localhost/jcms-testing/#/schema/WebPage/base",
            "url": "http://localhost/jcms-testing/index.php/en/article-en-gb",
            "name": "Article (en-gb)",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebSite/base"
            },
            "about": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            },
            "inLanguage": "en-GB",
            "breadcrumb": {
                "@id": "http://localhost/jcms-testing/#/schema/BreadcrumbList/139"
            }
        },
        {
            "@type": "Article",
            "headline": "Article Schema Test",
            "description": "Latin text used to simulate layouts.",
            "author": {
                "@type": "person",
                "name": "Superman"
            },
            "@id": "http://localhost/jcms-testing/#/schema/com_content/article/1",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebPage/base"
            }
        }
    ]
}</script>
```

Você pode testar seus dados estruturados na [página de teste de dados estruturados do Google](https://developers.google.com/search/docs/appearance/structured-data).

## Plugins disponíveis

| Plugin | Descrição |
|--------|-------------|
| Article Plugin | O ponto de partida para usar schema.org |
| Blogposting Plugin | Para conteúdo de Postagem de Blog |
| Book Plugin | Para conteúdo de Livro |
| Custom Plugin | Para entrada direta de código JSON-LD |
| Event Plugin | Para conteúdo de Evento |
| JobPosting Plugin | Para conteúdo de Anúncio de Emprego |
| Organization Plugin | Para conteúdo de Empresa e Organização |
| Person Plugin | Para conteúdo de Pessoa |
| Recipe Plugin | Para conteúdo de Receita |

*Traduzido por openai.com*

