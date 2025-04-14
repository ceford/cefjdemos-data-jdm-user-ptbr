<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: Noções básicas de SEO -->

## Definição

A Otimização para Motores de Busca é o processo de aprimorar uma ampla gama de características de um site com a intenção de melhorar a posição em que ele aparece nos motores de busca.

O processo de otimização de um site é multifacetado, pois há muitos fatores que afetam onde uma página pode se classificar em um mecanismo de busca.

- Garantindo que o conteúdo tenha estrutura apropriada usando HTML Semântico
- Melhorando a qualidade do conteúdo das páginas individuais.
- Garantindo que o site possa lidar com solicitações rapidamente.
- Habilitando URLs Amigáveis para Motores de Busca para tornar o endereço web das páginas *legível por humanos*.
- Adicionando Marcações Semânticas Contextuais usando dados do Schema.

Recurso: [Guia de Início de Otimização para Motores de Busca (SEO)](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)

## Estrutura do Site e URLs Descritivas

Nos primeiros dias, os sites eram estruturados como arquivos HTML individuais em uma hierarquia de árvore. Alguns sites ainda são estruturados dessa forma. CMSs são diferentes. Páginas individuais são montadas a partir de conteúdo armazenado em tabelas de banco de dados. Os URLs do primeiro e do segundo são diferentes, talvez assim:

```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```

Claramente, o primeiro é mais fácil de lembrar e mais fácil de digitar. Motores de busca preferem eles.

No CMS Joomla, uma URL da primeira forma pode ser configurada da seguinte maneira:

1. Crie uma Categoria de Conteúdo chamada **Usuário**.
2. Crie uma Categoria de Conteúdo chamada **SEO** que seja filha de *Usuário*.
3. Crie um artigo e atribua-o à categoria *SEO*.
4. Crie um item de menu **Usuário** do tipo **Lista de Categorias** usando a categoria *Usuário*.
5. Crie um item de menu **SEO** do tipo **Lista de Categorias** usando a categoria *SEO*.
6. Configure a funcionalidade de SEO do Joomla em *Configuração Global*.

Teste com o seu URL SEO: navegue pelas listas de Usuário e SEO até a página de Noções Básicas de SEO. Os Breadcrumbs devem mostrar: `Você está aqui: Início / Usuário / SEO / Noções Básicas de SEO`. Mas não se você criou um tipo de item de menu Artigo Único para *Noções Básicas de SEO*!

## Reduzir Duplicação

O problema com CMSs é que o mesmo conteúdo pode estar disponível com diferentes URLs. No exemplo acima, ambos os URLs funcionarão (mas não neste site), assim como `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Apenas um desses deve ser reconhecido pelos mecanismos de busca e definido como a URL **canônica**. Mas qual deles e como?

O plugin **Sistema - SEF** oferece alguma ajuda. Ele possui três configurações:

- **Domínio do Site** Se o seu site puder ser acessado através de mais de um domínio, insira aqui o domínio preferido (às vezes referido como canônico). **Nota:** `https://example.com` e `https://www.example.com` são domínios diferentes.
- **Tratamento rigoroso de index.php** Esta opção permite um tratamento mais rigoroso de `index.php` nas URLs quando **Usar Reescrita de URL** está ativado na Configuração Global. Isso removerá `index.php` se uma URL ainda o contiver e redirecionará as solicitações recebidas com `index.php` para a versão sem o `index.php`.
- **Barra final para URLs** Força o Joomla a usar apenas URLs com ou sem barra final. Quando configurado, isso forçará a URL correta com redirecionamentos e só é aplicado quando 'Adicionar sufixo à URL' está desativado.

Caso contrário, veja a explicação sobre **Tags Canônicas** por [Daniel Morell](https://www.danielmorell.com/blog/how-to-create-joomla-canonical-tags).

## Qualidade do Conteúdo

Faça o que você escreve ser interessante e fácil de ler. Parágrafos longos geralmente são opressivos e difíceis de ler. Parágrafos de uma linha parecem errados! Talvez eles devessem realmente ser pontos de lista. Mire em parágrafos de cerca de três linhas. Leia o que você escreve e edite qualquer palavra desnecessária.

Mantenha seu conteúdo atualizado e evite copiar informações de outros sites. Se possível, verifique seu conteúdo.

### HTML Semântico

O conteúdo deve consistir em uma hierarquia de títulos e parágrafos com outros elementos conforme necessário (listas, tabelas e assim por diante). Não confunda estrutura com aparência - portanto, não use um título para deixar o texto em negrito ou texto em negrito para criar um título. Este é um exemplo de marcação semântica de um artigo:

```html
  <h2>Using headings</h2>
  <p>This is an article about the importance of headings.</p>

  <h2>Why use headings?</h2>
  <p>It is important to use headings so that search engine bots can tell what
  is an <strong>important</strong> part of your article.</p>

  <h3>Types of headings</h3>
  <p>You can use set types of headings, but they should be ordered, and
  structured, within your page.  H1 will be the page title inserted by Joomla,
  with H2 being used for sub-headings of the page.  Any headings within your
  sub-headings should cascade using H3, H4, and H5 as appropriate.</p>

  <h2>Is it hard to implement headings?</h2>
  <p>It is really easy to implement headings, you just use the appropriate
  HTML code.</p>
```

Observe que um artigo *Título* se tornará um cabeçalho `<h1>` se necessário, portanto, não o use no corpo do artigo.

## Antecipar Termos de Pesquisa

Escolha títulos explícitos para suas páginas e cabeçalhos dentro das páginas. Por exemplo, se você não sabe o que é *HTML Semântico* ou quer mais informações sobre esse assunto, essas seriam as palavras que você digitaria em um mecanismo de busca. Pense nas pessoas que podem estar interessadas nas informações que você está fornecendo. O que elas vão procurar? Mas mantenha os Títulos e Cabeçalhos relativamente curtos - algumas fontes dizem no máximo 60 caracteres.

## Cuidado com os Anúncios

Nada afastará mais os visitantes do site do que anúncios aparecendo aqui, ali e em toda parte e movendo as informações reais diante de seus olhos. Anúncios que mudam a cada poucos segundos também são irritantes e consomem os recursos do usuário final. Muitos usarão bloqueadores de anúncios!

## Cuidado com Links

Links são tanto uma bênção quanto uma maldição! Eles podem afetar a classificação de SEO do seu site de forma positiva ou negativa, dependendo se você tem links para fontes respeitáveis ou não respeitáveis. E eles precisam ser mantidos. Você pode ter links para artigos internos ou externos que desapareceram, apresentam informações desatualizadas ou não são mais relevantes. Melhor conselho: coloque links se o destino adicionar um benefício real para os visitantes do seu site e use o atributo de link `nofollow` se você não quiser que o site de destino seja associado ao seu site.

Há muitas ferramentas de verificação de links disponíveis, algumas gratuitas ou freemium e outras pagas, muitas vezes como parte de um serviço de monitoramento de sites.

## Título da Página e Descrição

No `<head>` de cada página deve haver uma tag `<title>` e uma tag `<description>`. O Joomla torna muito fácil definir um título diferente para cada página. Infelizmente, também torna muito fácil negligenciar a definição de um Título e uma Descrição adequados em cada página.

Como exemplo, pegue a página de lista da categoria **SEO** mencionada acima. O `<title>` da fonte da página diz **SEO** e a `<description>` está ausente. No formulário **Menus: Editar Item** para este item de menu, há uma aba **Exibição de Página** com um campo **Título da Página do Navegador**. Insira `SEO - Lista de Artigos` lá e é isso que aparece na tag `<title>` e na aba do navegador.

Na aba **Metadados**, com o campo **Meta Description** definido como `Lista de artigos sobre Otimização de Motores de Busca.` é exatamente isso que aparece no campo `<description>`. A Descrição às vezes é usada para acompanhar um Título de página nos resultados de pesquisa, por isso deve ser relevante.

Mais informações:
* Artigo da revista: [Joomla SEO title tags](https://magazine.joomla.org/all-issues/september/joomla-seo-title-tags)
* [Explore o Núcleo: Opções de SEO Nativas](https://magazine.joomla.org/all-issues/june/explore-the-core-native-seo-options)

## Otimizar Imagens

Nem é preciso dizer que imagens atraentes podem melhorar enormemente um site. Mas muitas que são muito grandes atraem penalidades de SEO. Aqui estão algumas dicas:

- Coloque as imagens ao lado do texto que elas ilustram.
- Use texto **alt** descritivo.
- Use nomes de imagem separados por hífen, por exemplo, cat-on-hot-tin-roof.jpg.
- Use o tipo certo de imagem para o trabalho: png para pôsteres, jpg para fotografias.
- Use imagens responsivas - há um [plugin Joomla](https://responsive-images.dgrammatiko.dev/) que cria dinamicamente versões webp de imagens png e jpg em vários tamanhos.

*Traduzido por openai.com*

