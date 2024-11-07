<!-- Filename: jdocmanual?manual=user&heading=plugins&filename=about-plugins.md / Display title: Sobre Plugins -->

## Introdução

Plugins são extensões do Joomla! que fazem algo *nos bastidores* em resposta a um gatilho. Existem cerca de 160 plugins principais em mais de 20 grupos. Desenvolvedores de terceiros fornecem muitos mais. A imagem a seguir mostra o início da lista de plugins com o comprimento da lista definido para 5, para a conveniência da captura de tela.

![Lista de plugins](../../../en/images/plugins/plugins-list.png "Lista de plugins")

## Tipos de Plugins

Na pasta de plugins do seu site, você verá os tipos. Por exemplo, você verá uma pasta **content**, que contém plugins que manipulam conteúdo, e uma pasta **user**, que contém plugins relacionados a usuários. Você pode filtrar a lista por Tipo ou por Elemento, como *contact*, que pode incluir vários Tipos.

## Parâmetros do Plugin

Os plugins podem ter poucos ou muitos parâmetros. Por exemplo, o plugin *Content - Email Cloaking* oferece a escolha entre dois métodos de camuflagem, enquanto o plugin *Editors - TinyMCE* possui uma longa lista de parâmetros opcionais. Todos os plugins têm padrões adequados. Muitas vezes, tudo o que precisa ser feito é *Habilitar* ou *Desabilitar* um plugin específico conforme a necessidade surgir.

## Execução de Plugin

A execução do plugin é acionada por um *evento*. Por exemplo, o código que monta um artigo para exibição possui eventos chamados `onContentAfterTitle`, `onContentBeforeDisplay` e `onContentAfterDisplay`. Eles são usados para posicionar quaisquer campos definidos pelo usuário nos locais selecionados.  

## Plugins individuais

Poucos dos plugins individuais estão documentados aqui. Eles são cobertos pelo  
Tipo na página de Ajuda de cada plugin.

*Traduzido por openai.com*  

