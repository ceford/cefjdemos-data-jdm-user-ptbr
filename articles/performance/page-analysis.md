<!-- Filename: jdocmanual?manual=user&heading=performance&filename=page-analysis.md / Display title: Análise da Página -->

## Lighthouse

> O Lighthouse é uma ferramenta automatizada e de código aberto para melhorar a qualidade das páginas web. Você pode executá-la em qualquer página web, pública ou que exija autenticação. Ela realiza auditorias de desempenho, acessibilidade, aplicativos web progressivos, SEO e mais.

Está disponível como uma ferramenta adicional para Google Chrome e Firefox e pode ser executada a partir da linha de comando. Isso é útil para testes em um ambiente de desenvolvimento local.

Mais informações no site Lighthouse do Chrome para Desenvolvedores.

Você pode usar a ferramenta online pelo site PageSpeed Insights.

A captura de tela a seguir mostra a primeira parte do relatório do PageSpeed Insights:

![Relatório do PageSpeed Insights](../../../en/images/performance/performance-pagespeed-insights.png)

## Melhorias de Desempenho

A segunda parte do relatório sugere métodos para melhorar o desempenho:

* **Eliminar recursos que bloqueiam a renderização** - Economia potencial de 540 ms. Francamente, isso exige muito trabalho para pouca recompensa.
* **Habilitar compressão de texto** - Economia potencial de 11 KiB. Em Configuração Global, no painel do Servidor, configure a Compressão de Página GZip para *Sim*. Isso deixa pequenos arquivos JavaScript e CSS ainda a serem minimizados e comprimidos.
* **Reduzir CSS não utilizado** - Economia potencial de 62 KiB. Os culpados são template.min.css e joomla-fontawesome.min.css, mas isso implica personalizar o CSS para cada página do site, o que é um trabalho muito sujeito a erros para pouca recompensa.
* **Servir ativos estáticos com uma política de cache eficiente** - 21 recursos encontrados. Referências fornecidas, incluindo referências específicas do Joomla.

A mensagem geral é que algumas sugestões valem a pena serem corrigidas e outras não.

## Relatório de Mobile vs Desktop

O relatório de Desktop geralmente difere do relatório de Mobile. Alguns problemas adicionais identificados neste caso:

* **Dimensionar imagens corretamente** - Economia potencial de 48 KiB. A tag de imagem atualmente está otimizada com imagens em formato webp de 768 e 1200 pixels de largura. Parece que algo intermediário é necessário.

## Acessibilidade

* **Links não têm um nome discernível** Isso se refere às setas Esquerda e Direita na parte inferior da página que navegam para frente ou para trás. O texto foi deixado de fora para evitar problemas de tradução. Precisa ser repensado!
* **Os alvos de toque não têm tamanho ou espaçamento suficiente** Isso se refere ao tamanho dos itens do menu nas colunas esquerda e direita. Eles precisam de mais espaço vertical - é necessário um ajuste de CSS.

## Melhores Práticas e SEO

Embora ambos tenham obtido a pontuação 100 para Mobile e Desktop, eles precisam ser verificados novamente após cada alteração de design.

## Resumo

Todos os problemas neste site foram resolvidos, exceto por desmontar os arquivos CSS e minificar os pequenos componentes de arquivos Javascript e CSS.

*Traduzido por openai.com*  

