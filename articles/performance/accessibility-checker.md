<!-- Filename: jdocmanual?manual=user&heading=performance&filename=accessibility-checker.md / Display title: Verificador de Acessibilidade  -->

## Sistema - Verificador de Acessibilidade do Joomla

Este é um plugin principal que pode ser usado para verificar a acessibilidade ao criar conteúdo de artigos. A captura de tela a seguir mostra algumas configurações do plugin:

![Configurações do plugin](../../../en/images/performance/performance-jooa11y-plugin-form.png "Configurações do Plugin")

Com a opção **Mostrar Sempre** configurada para *Ligado*, o ícone do relatório aparece em cada página do site. Isso é útil para desenvolvimento, mas nunca deve ser deixado ativado em um site ao vivo. Defina como **Desligado**!

Com a opção *Mostrar Sempre* configurada para *Ligado*, cada página do site tem um ícone no canto inferior direito com uma contagem do número de problemas. A captura de tela a seguir mostra o ícone selecionado para exibir um painel de informações. Ele inclui um Resumo da Página, comentários de Leiturabilidade e Avisos, que podem ser selecionados um a um. O primeiro problema foi selecionado.

![Verificação de acessibilidade do site](../../../en/images/performance/performance-jooa11y-site-display.png "Verificação de acessibilidade do site")

O formulário de *Artigos: Edição* possui um botão de **Verificação de Acessibilidade** na Barra de Ferramentas. Ele mostra a verificação de um artigo individual em uma janela pop-up:

![Verificação de acessibilidade do editor](../../../en/images/performance/performance-jooa11y-admin-display.png "Verificação de acessibilidade do editor")

## Corrigindo Problemas

O Verificador de Acessibilidade é uma ferramenta para identificar problemas. Ele não corrige problemas. Isso cabe a você. O verificador possui algumas configurações que você pode alternar Ligado/Desligado conforme necessário. Elas incluem Contraste, Rótulos de Formulário, Links (Avançado) AAA, Legibilidade AAA, Modo Escuro e Filtro de Cor com simulação de quatro tipos de visão de cor defeituosa.

Para mais informações, consulte a Visão Geral do Sa11y

Por exemplo, sobre Legibilidade, ele diz:

> O Sa11y pode estimar a pontuação de legibilidade a partir de todos os parágrafos e conteúdos de lista. Uma boa pontuação de legibilidade é um indicativo de que sua escrita é compreensível e fácil de digerir. Baseia-se no comprimento médio das frases e palavras em sua página, usando uma fórmula conhecida como teste de legibilidade de Flesch (Wikipedia). Uma pontuação de leitura "boa" está entre 60 e 100. Às vezes pode ser difícil alcançar uma boa pontuação de legibilidade. A maioria das suas páginas pode dizer "difícil". Lembre-se de que este recurso é apenas para estimar a legibilidade do seu conteúdo. Deve ser usado apenas como referência e não como uma indicação de conformidade. O Sa11y calcula a pontuação de legibilidade com base em todo o conteúdo de parágrafos (tags `<p>`) e listas (tags `<li>`). Uma pontuação baixa não afeta o estado de aprovação ou reprovação do Sa11y.

*Traduzido por openai.com*

