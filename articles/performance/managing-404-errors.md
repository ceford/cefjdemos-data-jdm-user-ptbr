<!-- Filename: Managing_404_Errors / Display title: Gerenciando Erros 404  -->

## Por Que o Erro 404 Não Encontrado Importa

O problema mais comum com sites que estão lutando para subir nos rankings dos mecanismos de busca é o número de erros de 'não encontrado' – comumente referidos como erros *404* porque esse é o código de status retornado se a página não puder ser encontrada.

Primeiro, há razões legítimas para ter erros 404 – se você tem uma página para um evento que já passou ou um serviço que você não fornece mais. Nesses casos, eventualmente a página será removida do índice dos mecanismos de busca e não estará mais associada ao seu site.

O problema ocorre se você tem muitos erros 404 – por exemplo, se você retirar do ar uma categoria que continha centenas de artigos. Do ponto de vista do mecanismo de busca, isso não é uma boa experiência para os visitantes deles, porque eles chegam ao seu site e a informação que o mecanismo de busca lhes disse estar lá, não está. Por isso, não é uma boa ideia ter muitos erros 404 no seu site.

## Google Search Central

O primeiro passo é descobrir quantos você tem – o que pode ser feito usando o [Search Central](https://developers.google.com/search) do Google. Este é um conjunto de ferramentas gratuitas que permite analisar seu site e identificar rapidamente problemas, erros e questões. Recomenda-se que você tenha todos os sites que gerencia registrados no Search Central para garantir que você seja notificado em caso de quaisquer problemas.

Quando você visita o Search Central, há uma seção que mostra os Erros de URL na listagem de pesquisa – isso exibirá uma lista dos erros 404 que o Google encontrou no seu site, e um gráfico que mostra como isso mudou ao longo do tempo. Se o gráfico começar a subir, investigue por que há páginas que estavam no seu site e agora não podem ser encontradas.

Se houve um problema temporário no seu site, você pode marcar os erros como corrigidos.

![ferramentas para webmasters](../../../en/images/performance/404-discovery.png)

## Corrigindo Problemas

A descoberta é apenas uma parte do processo. Uma vez que você tenha descoberto os URLs problemáticos, faça algo a respeito (se precisar ser corrigido!) redirecionando a página para outra no site, reinstaurando a página original ou investigando o que causou o erro 404.

Se você precisar redirecionar uma página, pode usar o plugin System - Redirect para coletar páginas ausentes e o componente System / Redirects para redirecionar páginas ausentes para páginas existentes.

## Monitoramento de Problemas

Se você deseja monitorar o tráfego de 404, a melhor maneira de fazer isso no Analytics é observar o que acontece quando você tem um erro 404. Na maioria dos casos, o título da página muda para 404 – então podemos criar um segmento personalizado que filtrará o tráfego com um título de 404 e informará qual é a página de entrada. Isso deve permitir que você monitore e gerencie proativamente seus erros 404 e garanta que os visitantes do seu site não acabem em links quebrados.

![Alertas de Analytics do tráfego 404](../../../en/images/performance/404-analytics-alerts.png)

![Visão geral de público do Analytics](../../../en/images/performance/404-analytics-alerts-2.png)

O Google também tem a capacidade, no Analytics, de configurar alertas. Alertas permitem que você seja notificado por e-mail quando certos eventos ocorrem. Neste caso, podemos configurar um alerta para ser notificado se houver um aumento de mais de 5% no número de erros 404 em um período semanal – o que pode significar que temos um problema com o site que precisa ser investigado.

Esta é uma ótima maneira de manter tudo sob controle, mesmo que você não tenha feito login para olhar seu painel!

![Email de alertas do Analytics](../../../en/images/performance/404-analytics-alerts-email.png)

## Monitorando Erros com um Dashboard

Existe um dashboard que você pode instalar chamado *Data Integrity Dashboard*, que mostra informações sobre erros 404, junto com algumas outras métricas que podem ser de seu interesse. Basta procurar na Galeria do Google Analytics por *Data Integrity Dashboard* e selecionar em qual perfil instalá-lo.

![Integridade de dados](../../../en/images/performance/404-data-integrity.png)

*Traduzido por openai.com*

