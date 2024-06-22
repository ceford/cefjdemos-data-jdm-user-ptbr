<!-- Filename: J4.x:Workflow / Display title: Fluxo de trabalho -->

Joomla!  4.x

## Introdução

O componente de fluxo de trabalho de publicação é usado para substituir
estados estáticos (não publicado, publicado, lixeira e arquivado) por
uma abordagem mais genérica. Dessa forma, você pode criar facilmente um
fluxo de trabalho personalizado para gerenciar seus artigos em um
componente.

- A visualização de back-end do artigo no Joomla 3.x:

<img
src="https://docs.joomla.org/images/thumb/a/a4/Article_view_3-en.png/800px-Article_view_3-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/a/a4/Article_view_3-en.png/1200px-Article_view_3-en.png 1.5x, https://docs.joomla.org/images/thumb/a/a4/Article_view_3-en.png/1600px-Article_view_3-en.png 2x"
data-file-width="2538" data-file-height="766" width="800" height="241"
alt="Article view 3-en.png" />

- A visualização de back-end de artigo no Joomla 4.x:

<img
src="https://docs.joomla.org/images/thumb/9/94/J4_Articles_Backend-en.png/800px-J4_Articles_Backend-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/9/94/J4_Articles_Backend-en.png 1.5x"
data-file-width="1200" data-file-height="332" width="800" height="221"
alt="J4 Articles Backend-en.png" />

A gama de ferramentas de artigo agora é menor e a visualização
geralmente mais organizada. Você pode criar estados personalizados para
os artigos e agrupá-los em categorias.

Há uma página de tutorial contendo os passos para a criação de seu
primeiro fluxo de trabalho:
Cenários.
Você pode encontrar mais informações sobre a implementação do componente
em outras áreas na página do Google summer of code project DOC:
Você pode desativar fluxos de trabalho a qualquer momento visitando
"artigos" ou "fluxos de trabalho" e clicando em "opções" no canto
superior direito. Alterne para a guia de "integração" e role para baixo
até "habilitar fluxo de trabalho".

## Termos e definições

- *Fluxos de trabalho:* Você pode criar vários fluxos de trabalho. Cada
  fluxo de trabalho contém estados, possíveis transições e condições de
  itens.
- *Estágios:* Os estágios são os pontos iniciais e finais de um fluxo de
  trabalho.
- *Estado:* O estado de um item pode ser não publicado, publicado,
  lixeira ou arquivado. Um estado pode ser alterado executando uma
  transição
- *Transições:* As transições ocorrem entre os estágios. Elas são onde
  as ações acontecem.
- *Categorias:* Os artigos podem ser atribuídos à categorias.

## Fluxos de trabalho

O fluxo de trabalho se assemelha à uma sequência de passos. Ele pode ser
acessado através do menu superior principal em "conteúdo". Você será
direcionado para a "lista de fluxos de trabalho", uma visão geral de
todos os seus fluxos de trabalho existentes. Um fluxo de trabalho contém
vários estados de diferentes condições. Itens (por exemplo, artigos)
podem transitar por esses estados.

<img
src="https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/800px-Workflows-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/1200px-Workflows-en.png 1.5x, https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/1600px-Workflows-en.png 2x"
data-file-width="1906" data-file-height="455" width="800" height="191"
alt="Workflows List" />

- Você vê o estado do fluxo de trabalho (publicado / não publicado)
- Ao lado do estado está o título. Ao clicar no título, você pode
  *editar o fluxo de trabalho*
  - *Editável*: título \| descrição \| estado \| opção padrão \|
    permissões (gerenciamento de direitos)
- Ao lado do título, você encontra a opção de *gerenciar* os passos do
  fluxo de trabalho (para obter mais informações, consulte
  Estágios
- Ao lado dos "estágios" está a opção padrão
- Você encontra um ícone amarelo, ao lado de "padrão", representando o
  número de estágios existentes neste fluxo de trabalho
- Ao lado do círculo amarelo está um ícone azul que representa o número
  de transições existentes neste fluxo de trabalho (para mais
  informações consulte
  Transições
- Você também pode ver o identificador (ID) do fluxo de trabalho.

## Estágios

Os estágios são acessados através do contêiner "lista de fluxos de
trabalho" clicando no ícone amarelo que mostra o número de estágios.
Você pode editar o nome de um estágio clicando nele.


<img
src="https://docs.joomla.org/images/thumb/a/ac/Stages-en.png/800px-Stages-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/a/ac/Stages-en.png 1.5x"
data-file-width="1200" data-file-height="251" width="800" height="167"
alt="Stages View" />

<img
src="https://docs.joomla.org/images/thumb/7/7f/Stages--edit-en.png/800px-Stages--edit-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/7/7f/Stages--edit-en.png 1.5x"
data-file-width="1200" data-file-height="404" width="800" height="269"
alt="The Edit Stage view" />

- Na segunda imagem você pode editar o estágio. Você pode habilitá-lo ou
  desabilitá-lo e escrever uma nota. Ali também tem uma alternância
  "padrão". Se houver apenas um item, você não poderá alterná-lo.

## Transições

Os artigos podem transitar de um estágio para outro. As transições podem
ser gerenciadas através do contêiner "lista de fluxos de trabalho"
clicando no ícone azul. Você pode definir várias transições pelas quais
os itens podem passar. Os estágios possíveis são baseados naqueles que
você criou para esse fluxo de trabalho específico.

O *estágio atual* definirá onde essa transição será aplicada. Você pode
escolher todos os estágios ou um estágio específico.

O *estágio alvo (de destino)* é o estágio em que o fluxo de trabalho
terminará após a transição.

<img
src="https://docs.joomla.org/images/thumb/4/45/Transitions--edit--description-en.png/800px-Transitions--edit--description-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/4/45/Transitions--edit--description-en.png 1.5x"
data-file-width="1200" data-file-height="456" width="800" height="304"
alt="Edit Transitions View" />

A guia de *ações de transição* permite definir em que estado o item
ficará após a conclusão da transição. Por exemplo, se o item for um
artigo, ele pode se tornar não publicado, o que é exatamente o que
acontece na transição *despublicar*. Você também pode definir se o item
é apresentado ou não até o final do estado.

<img
src="https://docs.joomla.org/images/thumb/2/27/Transitions--edit--transition-actions-en.png/800px-Transitions--edit--transition-actions-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/2/27/Transitions--edit--transition-actions-en.png 1.5x"
data-file-width="1200" data-file-height="429" width="800" height="286"
alt="Edit Transition Actions" />

A guia de *notificações de transição* permite definir se uma notificação
é enviada durante esse estado. Por exemplo, se um artigo foi escrito,
mas precisa ser revisado, você pode enviar uma notificação por e-mail ao
editor.

Você também pode adicionar texto de mensagem adicional. Isso também
permitirá que você use uma  string de
linguagem
que tornaria o texto da mensagem traduzível.

A opção de grupos de usuários permitirá definir quem receberá a
notificação. No exemplo que escolhemos, escolheríamos *editor* como o
grupo de usuários. Nesse exemplo, todos os usuários desse grupo de
usuários receberiam uma notificação.

Finalmente, há a opção para "mais receptores". Isso permite que você
escolha usuários individuais para receber essa notificação.

<img
src="https://docs.joomla.org/images/thumb/5/57/Transitions--edit--notification-en.png/800px-Transitions--edit--notification-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/5/57/Transitions--edit--notification-en.png 1.5x"
data-file-width="1200" data-file-height="481" width="800" height="321"
alt="Edit Transition Notification" />

A guia final é a guia de permissões. Isso permite que você defina quem
pode usar essa transição.

- *Exemplo:* Na transição "próximo passo: publicação" os itens são
  originalmente do estado "não publicado". Eles estão, por exemplo,
  precisando de uma revisão. Depois de revisados, podem transitar para o
  estado "publicado".
- Todas as ações de transição de fluxo de trabalho são plug-ins de fluxo
  de trabalho do Joomla!. Se você for a sistema **→** plugins e, em
  seguida, alterar o menu suspenso de "tipo" para o de "fluxo de
  trabalho", você verá os plugins. Eles podem ser desabilitados como
  qualquer outro plugin.

<img
src="https://docs.joomla.org/images/thumb/9/96/Workflows--plugins--workflows-en.png/800px-Workflows--plugins--workflows-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/9/96/Workflows--plugins--workflows-en.png 1.5x"
data-file-width="1200" data-file-height="358" width="800" height="239"
alt="Workflows Plugins" />

## Categorias

Os artigos podem ser atribuídos à categorias. Elas correspondem a um
determinado fluxo de trabalho e podem ser personalizadas de várias
maneiras. Você pode definir um estado, a categoria pai e também
restringir o acesso e as permissões. Essa opção não está na tela de
fluxos de trabalho. Para esta opção você precisa ir para
conteúdo **→** categorias. Uma vez lá, abra qualquer categoria e você
verá uma guia de "fluxos de trabalho".

- *Exemplo:* Você tem certos artigos que deseja que estejam disponíveis
  apenas para administradores ou usuários de nível superior. Você pode
  chamar sua categoria de "estrita" e definir todas as permissões como
  "permitidas" para administradores ou superiores. Dessa forma, você não
  precisa definir essas permissões para todos os artigos em questão, mas
  pode movê-los para essa categoria especial e economizar tempo.

<img
src="https://docs.joomla.org/images/thumb/d/dd/Workflow-categories-en.png/800px-Workflow-categories-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/d/dd/Workflow-categories-en.png 1.5x"
data-file-width="1200" data-file-height="431" width="800" height="287"
alt="Workflow-categories-en.png" />

## Controle de versão

Quando o fluxo de trabalho é habilitado, os campos gerenciados pelo
fluxo de trabalho são excluídos do controle de versão (como "estado" e
"em destaque") para evitar conflitos de permissão.

## Informações relacionadas

Consulte também:

-  Implementação do fluxo de trabalho de
  publicação
- Cenários
