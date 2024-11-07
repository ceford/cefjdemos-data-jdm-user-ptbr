<!-- Filename: Keyboard_Shortcuts / Display title: Atalhos de Teclado -->

## Introdução

O teclado pode ser usado na interface do Administrador para invocar algumas das ações geralmente realizadas com um mouse ou touchpad. Por exemplo, há atalhos de teclado para salvar a página atual, ir para o *Painel Inicial* ou abrir um formulário de *Opções*.

Há uma visão geral de todos os atalhos, aberta pela seleção sequencial do teclado das teclas **J** e **X** (não ao mesmo tempo e não use a tecla Shift normalmente usada para capitalização). A menos que você altere as configurações do plugin, você deve pressionar as teclas em até 2 segundos.

O recurso é habilitado por padrão. Ele pode ser desabilitado ou configurado em **Administrador → Sistema → Plugins → Sistema - Atalhos de Teclado**. Atualmente, a única configuração é o tempo limite: quanto tempo o sistema aguardará pela sua próxima entrada de tecla. Por padrão, ele espera 2000 milissegundos (2 segundos).

## Atalhos Padrão no Joomla

- J + A - Salvar conteúdo atual
- J + S - Para Salvar & Fechar
- J + Q - Cancela a página atual
- J + N - Pressiona o botão *Novo*
- J + F - Foca no campo de Pesquisa
- J + O - Vai para Opções
- J + H - Abre a janela de Ajuda (pode acionar um aviso de pop-up do navegador)
- J + M - Alterna a barra de menu
- J + X - Exibe uma lista de Atalhos disponíveis
- J + D - Vai diretamente para o Painel Inicial

## Atalhos de Terceiros - Informações para Desenvolvedores

Outros desenvolvedores também podem adicionar seus atalhos. O plugin do Joomla chama o Evento *onLoadShortcuts*, que também pode ser utilizado por outros plugins. O evento precisa ser adicionado à lista de *getSubscribedEvents* dentro do plugin. A função atribuída poderia se parecer com isso:

```php
    public function onLoadShortcuts(EventInterface $event): void {
       $shortcuts = $event->getArgument('shortcuts');
       $exampleShortcuts = array('example' => (object)['shortcut' => 'E', 'title' => 'Ótimo Exemplo', 'selector' => '#menu-collapse']);
       $event->setArgument('shortcuts',  array_merge($shortcuts, $exampleShortcuts));
    }
```

Preste muita atenção à parte do array_merge: quando os atalhos já existentes não são mesclados com os novos, os antigos são sobrescritos.

Os desenvolvedores podem fornecer um array com objetos de atalho:

    { shortcut: string, selector: string, title: string }

- O *Atalho* precisa ser uma entrada de teclado, separada por um mais, por exemplo, `Y` ou `ALT + Z + 7` (atualmente, realmente não há filtragem). Lembre-se de que toda sequência de atalho começará com **J**.
- *Seletores* são seletores CSS ou URLs para especificar o alvo. Quando é um elemento de entrada, o atalho dá foco, como é o caso do campo de busca. Caso contrário, o elemento será clicado ou a URL será chamada.
- O *Título* será exibido no resumo. Ele poderia ser, por exemplo, o nome do alvo.

## Razões para usar J + X

Alguns podem se perguntar sobre a decisão de usar atalhos sequenciais ou o **J** como início, em vez de Ctrl ou algo assim. As principais razões são acessibilidade e a prevenção de interrupção por outros softwares. Por exemplo, *Ctrl + S* seria bom para salvar um artigo, mas já é usado pelos navegadores. O mesmo pode acontecer para leitores de tela ou gerenciadores de senhas. Portanto, a opção mais segura foi usar algo específico do Joomla, como o **J** no início.

Agora, o outro problema é que nem sempre é possível pressionar mais de uma tecla ao mesmo tempo. O Windows tem o modo Teclas de Aderência para isso, mas ele funciona apenas para teclas modificadoras como Shift, Ctrl e Alt. Assim, o plugin utiliza a entrada sequencial desde o início, o que o torna utilizável por mais pessoas, mesmo sem a ajuda de modos do sistema operacional.

*Traduzido por openai.com*  

