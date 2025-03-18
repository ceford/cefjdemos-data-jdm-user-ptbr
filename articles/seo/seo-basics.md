<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: Noções Básicas de SEO -->

## Definição

A Otimização para Mecanismos de Busca (SEO) é o processo de melhorar uma ampla gama de características de um site com a intenção de melhorar a posição em que ele aparece nos mecanismos de busca.

O processo de otimização de um site é multifacetado, pois há muitos fatores que afetam onde uma página pode ser classificada em um mecanismo de busca.

- Garantir que o conteúdo tenha uma estrutura apropriada usando HTML Semântico
- Melhorar a qualidade do conteúdo de páginas individuais.
- Assegurar que o site possa lidar com solicitações rapidamente
- Habilitar URLs Amigáveis para Motores de Busca para tornar o endereço das páginas 'legível por humanos'
- Adicionar Marcação Semântica Contextual usando dados de Schema

Recurso: Guia para Iniciantes em Otimização para Mecanismos de Busca (SEO)

## Estrutura do Site e URLs Descritivos

Nos primeiros dias, os sites eram estruturados como arquivos HTML individuais em uma hierarquia de árvore. Alguns sites ainda são estruturados dessa forma. CMSs são diferentes. Páginas individuais são montadas a partir de conteúdo armazenado em tabelas de banco de dados. As URLs para o primeiro e o último caso são diferentes, talvez como esta:
```
https://www.exemplo.com/usuario/seo/basico-seo.html
https://www.exemplo.com/index.php?option=com_jdocmanual&view=manual&manual=usuario&heading=seo&filename=basico-seo
```
Claramente, a primeira é mais fácil de lembrar e digitar. Motores de busca preferem elas.

No CMS Joomla, uma URL do primeiro formato pode ser configurada da seguinte maneira:

1. Crie uma Categoria de Conteúdo chamada **Usuário**.
2. Crie uma Categoria de Conteúdo chamada **SEO**, que seja filha de *Usuário*.
3. Crie um artigo e atribua-o à categoria *SEO*.
4. Crie um item de menu **Usuário** do tipo **Lista de Categoria** usando a categoria *Usuário*.
5. Crie um item de menu **SEO** do tipo **Lista de Categoria** usando a categoria *SEO*.
6. Configure a funcionalidade SEO do Joomla em *Configuração Global*.

Teste com sua URL SEO: navegue pelas listas de Usuário e SEO até a página de SEO Básico. O Breadcrumbs deve mostrar: `Você está aqui: Início / Usuário / SEO / SEO Básico`. Mas não se você criou um item de menu do tipo Artigo Único para *SEO Básico*!

## Reduzir Duplicação

O problema com os CMSs é que o mesmo conteúdo pode estar disponível com diferentes URLs. No exemplo acima, ambas as URLs funcionarão (mas não neste site), assim como `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Apenas uma dessas deve ser reconhecida pelos motores de busca e definida como a URL **canônica**. Mas qual e como?

O plugin **System - SEF** oferece alguma ajuda. Ele possui três configurações:

* **Domínio do Site:** Se seu site pode ser acessado por mais de um domínio, insira aqui o domínio preferido (às vezes referido como canônico). **Nota:** `https://example.com` e `https://www.example.com` são domínios diferentes.
* **Manipulação estrita do index.php:** Esta opção permite uma manipulação mais estrita de 'index.php' nas URLs quando 'Reescrita de URL' está ativada na Configuração Global. Ela removerá 'index.php' se uma URL ainda o contiver e redirecionará solicitações de entrada com 'index.php' para a versão sem o 'index.php'.
* **Barra no final das URLs:** Força o Joomla a usar apenas URLs com ou sem barra final. Quando configurado, isso forçará a URL correta com redirecionamentos e só será aplicado quando 'Adicionar sufixo à URL' estiver desativado.

Explicação de **Tags Canônicas** por Daniel Morell:

* Como Criar Tags Canônicas no Joomla
* Plugin e Documentação:

Para Joomla 4 e 5, antes de ativar, é necessário alterar `if ($app->isAdmin()) {` para `if ($app->isClient('admin')) {` nas linhas 72 e 99 de *plugins/system/customcanonical/customcanonical.php*.

Em um artigo, selecione a aba Publicação e, em seguida, o botão **Auto** da *URL Canônica*. Isso irá colocar um link como o seguinte em qualquer página que exiba o artigo único:
```
    <link href="/jdm3/en/user/seo/seo-basics.html" rel="canonical" />
```

## Qualidade do Conteúdo

Faça o que você escreve ser interessante e fácil de ler. Parágrafos longos costumam ser avassaladores e difíceis de ler. Parágrafos de uma linha parecem errados! Talvez eles realmente devam ser pontos em lista. Mire para parágrafos de cerca de três linhas. Leia o que você escreve e edite para remover quaisquer palavras desnecessárias.

Mantenha seu conteúdo atualizado e evite copiar informações de outros sites. Se possível, verifique seu conteúdo.

### HTML Semântico

O conteúdo deve consistir em uma hierarquia de cabeçalhos e parágrafos com outros elementos conforme necessário (listas, tabelas e assim por diante). Não confunda estrutura com aparência - portanto, não use um cabeçalho para negrito ou negrito para um cabeçalho. Este é um exemplo de marcação semântica de um artigo:

```html
  <h2>Usando cabeçalhos</h2>
  <p>Este é um artigo sobre a importância dos cabeçalhos.</p>

  <h2>Por que usar cabeçalhos?</h2>
  <p>É importante usar cabeçalhos para que os robôs dos motores de busca possam identificar qual é a parte <strong>importante</strong> do seu artigo.</p>

  <h3>Tipos de cabeçalhos</h3>
  <p>Você pode usar tipos definidos de cabeçalhos, mas eles devem ser ordenados e estruturados dentro da sua página. O H1 será o título da página inserido pelo Joomla, com o H2 sendo usado para subcabeçalhos da página. Quaisquer cabeçalhos dentro dos seus subcabeçalhos devem ser em cascata usando H3, H4 e H5 conforme apropriado.</p>

  <h2>É difícil implementar cabeçalhos?</h2>
  <p>É muito fácil implementar cabeçalhos, você só precisa usar o código HTML apropriado.</p>
```

Observe que um *Título* de artigo se tornará um cabeçalho `<h1>` se necessário, então não o use no corpo de um artigo.

## Preveja Termos de Pesquisa

Escolha títulos explícitos para suas páginas e cabeçalhos dentro das páginas. Por exemplo, se você não sabe o que é *HTML Semântico* ou quer mais informações sobre esse assunto, essas seriam as palavras que você digitaria em um mecanismo de busca. Pense nas pessoas que possam estar interessadas nas informações que você está fornecendo. O que elas buscarão? Mas mantenha os Títulos e Cabeçalhos relativamente curtos – algumas fontes dizem que não devem ter mais do que 60 caracteres.

## Cuidado com Anúncios

Nada afastará mais os visitantes do site do que anúncios aparecendo aqui, ali e em todo lugar, movendo a informação real diante dos seus olhos. Anúncios que mudam a cada poucos segundos também são irritantes e consomem os recursos do usuário final. Muitos utilizarão bloqueadores de anúncios!

## Cuidado com Links

Os links são uma bênção e uma maldição! Eles podem afetar a classificação de SEO do seu site para melhor ou pior, dependendo se você tem links para fontes respeitáveis ou não. E eles precisam ser mantidos. Você pode ter links para artigos internos ou externos que desapareceram, apresentam informações desatualizadas ou não são mais relevantes. Melhor conselho: faça um link se o destino adicionar um benefício real para os visitantes do seu site e use o atributo de link `nofollow` se você não quiser que o site de destino seja associado ao seu site.

Existem muitas ferramentas de verificação de links disponíveis, algumas gratuitas ou freemium e outras pagas, muitas vezes como parte de um serviço de monitoramento de sites.

## Título da Página e Descrição

No `<head>` de cada página, deve haver uma tag `<title>` e uma tag `<description>`. O Joomla torna muito fácil definir um título diferente para cada página. Infelizmente, também é muito fácil negligenciar a definição de um Título e Descrição adequados em cada página.

Como exemplo, considere a página de lista da categoria **SEO** mencionada acima. No código-fonte da página, o `<title>` diz **SEO** e a `<description>` está ausente. No formulário **Menus: Editar Item** para este item de menu, há uma aba **Exibição da Página** com um campo **Título da Página do Navegador**. Insira `SEO - Lista de Artigos` lá e é isso que aparece na tag `<title>` e na aba do navegador.

Na aba **Metadados**, com o campo **Descrição Meta** definido como `Lista de artigos sobre Otimização para Motores de Busca.`, isso é exatamente o que aparece no campo `<description>`. Às vezes, a Descrição é usada para acompanhar um Título de página nos resultados de busca, por isso deve ser relevante.

Mais informações:
* Artigo de revista: Tags de título de SEO no Joomla
* Explore o Core: Opções nativas de SEO

## Otimize Imagens

Nem é preciso dizer que imagens atraentes podem melhorar enormemente um site. No entanto, muitas imagens que são muito grandes atraem penalidades de SEO. Aqui estão algumas dicas:

* Coloque as imagens próximas ao texto que elas ilustram.
* Use um texto **alt** descritivo.
* Use palavras separadas por hífen para os nomes das imagens, por exemplo, gato-no-telhado-quente.jpg.
* Use o tipo certo de imagem para o trabalho: png para cartazes, jpg para fotografias.
* Use imagens responsivas - há um plugin no Joomla que cria dinamicamente versões webp de imagens png e jpg em vários tamanhos.

*Traduzido por openai.com*
