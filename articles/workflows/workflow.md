<!-- Filename: J4.x:Workflow / Display title: Fluxo de Publicação   -->

## Introdução

No Joomla, um fluxo de trabalho é uma sequência de etapas na vida de um artigo, desde a concepção até a sua conclusão. As etapas geralmente são realizadas por diferentes indivíduos com diferentes responsabilidades. Por exemplo, no mundo dos jornais, um subeditor recebe uma matéria de um repórter e verifica a precisão, gramática, legibilidade e comprimento, entre outros. O subeditor então passa a reportagem para o editor, que pode aceitá-la ou rejeitá-la, decidir onde colocá-la no jornal, e assim por diante.

O componente de Fluxo de Trabalho é usado para adicionar **estágios** aos artigos para aprimorar os estados estáticos (não publicado, publicado, descartado e arquivado) com **transições**. Os estados estáticos e as transições são registrados separadamente para que os Fluxos de Trabalho possam ser ativados ou desativados conforme necessário, sem afetar o estado dos itens de conteúdo. Os Fluxos de Trabalho são ativados ou desativados na aba *Integração* da página *Artigos: Opções*. 

Há uma página de tutorial contendo etapas para a criação de um exemplo de fluxo de trabalho: [Cenários de Fluxo de Trabalho](jdocmanual?article=user/workflows/workflow-scenarios).  

## Termos e Definições

- *Fluxo de Trabalho:* Um fluxo de trabalho é uma sequência completa de etapas. Diferentes fluxos de trabalho podem ser criados para diferentes propósitos. O componente de Fluxo de Trabalho contém um *Fluxo de Trabalho Básico* e os dados de exemplo do Blog têm um *Fluxo de Trabalho de Blog* mais complexo.
- *Etapa:* Uma etapa é um local dentro de um fluxo de trabalho. Por exemplo, um artigo não publicado pode estar na Etapa 1: Em Preparação ou Etapa 2: Pronto para Revisão, e assim por diante. É a etapa do item que é registrada no banco de dados.
- *Transição:* Uma transição é uma mudança de uma etapa para outra, muitas vezes para a próxima no fluxo de trabalho, mas pode ser para a etapa anterior ou etapa inicial.
- *Estado:* O estado de um artigo pode ser não publicado, publicado, descartado ou arquivado. Um estado pode ser alterado executando uma transição de fluxo de trabalho, desde que o usuário tenha permissão para mudar de estado.
- *Categoria:* Quando os fluxos de trabalho estão em uso, um Fluxe de Trabalho específico pode ser selecionado para uma categoria na aba *Fluxo de Trabalho* do formulário *Artigo: Editar Categoria*.

## A Lista de Fluxos de Trabalho

Quando os fluxos de trabalho estão habilitados, a lista de fluxos de trabalho disponíveis pode ser vista selecionando **Conteúdo → Fluxos de Trabalho** no menu do Administrador.

![Lista de fluxos de trabalho](../../../en/images/workflows/workflows-list.png)

- O **Status** de um fluxo de trabalho pode ser Habilitado, Desabilitado ou Excluído.
- O **Nome** é um link para o formulário de edição do fluxo de trabalho.
- O item **Padrão** é usado para novos itens que não estão atribuídos a uma categoria que possui um fluxo de trabalho definido.
- O item **Etapas** é um botão que mostra o número de etapas e um link para a lista de etapas do fluxo de trabalho.
- O item **Transições** é um botão que mostra o número de transições e um link para a lista de transições do fluxo de trabalho.
- O **ID** é o valor numérico do fluxo de trabalho usado internamente.

## Etapas

As etapas são acessadas através da lista de *Fluxos de Trabalho*. Selecione o botão amarelo que mostra o número de etapas.

![Lista de etapas do fluxo de trabalho](../../../en/images/workflows/workflow-stages-list.png)

Selecione o nome de uma etapa para editá-la.

![Formulário de edição da etapa do fluxo de trabalho](../../../en/images/workflows/workflow-stage-edit.png)

## Transições

Nos fluxos de trabalho, os artigos passam de uma etapa para outra. As transições são gerenciadas por meio da lista de *Transições*.

![A lista de transições](../../../en/images/workflows/workflow-transitions-list.png)

- O *Estágio Atual* define onde começa esta transição.
- O *Estágio Alvo* define onde termina esta transição.

### Estágios de Transição

Os estágios *Atual* e *Alvo* são definidos no formulário *Editar Transição*:

![Formulário de edição de transição](../../../en/images/workflows/workflow-transition-edit.png)

A aba *Ações de Transição* é usada para definir o *Estado* em que o item estará após a conclusão da transição.

![Aba de ações do formulário de edição de transição](../../../en/images/workflows/workflow-transition-edit-actions-tab.png)

- **Estado de Destaque** Determina se o item será ou não *Destacado*.
- **Estado de Publicação** Selecione na lista o estado de destino.

A aba *Notificações de Transição* é usada para definir se uma notificação será enviada para aquele estado. Por exemplo, se um artigo foi escrito mas precisa ser revisado, um e-mail pode ser enviado para notificar o editor.

![Aba de notificações do formulário de edição de transição](../../../en/images/workflows/workflow-transition-edit-notifications-tab.png)

- **Enviar Notificação** Se definido como *Sim*, campos extras aparecem.
- **Texto de Mensagem Adicional** Adicione um texto de mensagem adicional ou use uma string de idioma para tornar o texto da mensagem traduzível.
- **Grupos de Usuários** Selecione quem receberá a notificação, por exemplo, todos os usuários no grupo de usuários *Editor*.
- **Usuários** Selecione usuários individuais para receber esta notificação.

### Permissões

A aba de permissões controla o acesso a esta transição por grupos de usuários selecionados. Normalmente, as permissões são herdadas das configurações de permissão em *Artigos: Opções*.

### Plugins de Transição de Fluxo de Trabalho

Os plugins de fluxo de trabalho são usados para ações invocadas por transições. Vá para **Sistema → Plugins** e altere o filtro *- Selecionar Tipo -* para *fluxo de trabalho*. Cada um desses plugins pode ser desativado, se não necessário.

![Lista de plugins de fluxo de trabalho](../../../en/images/workflows/workflow-plugins.png)

- **Destaque de Fluxo de Trabalho** Esta ação implementa a mudança do status de *Destacado* de um artigo de *Sim* para *Não*.
- **Notificação de Fluxo de Trabalho** Esta ação implementa a notificação a um usuário de que uma mudança de estágio requer atenção.
- **Publicação de Fluxo de Trabalho** Esta ação implementa uma mudança de estado de um artigo de um para outro dos estados *Publicado*, *Não Publicado*, *Descartado* ou *Arquivado*. Se o usuário não tiver permissão para mudar de estado, falhará com uma mensagem explicativa. A transição que solicitou a mudança de estado ainda será bem-sucedida!

## Categorias

Os artigos podem ser atribuídos a categorias. Elas correspondem a um determinado fluxo de trabalho e podem ser personalizadas de várias maneiras. Você pode definir um status, categoria pai e também restringir o acesso, bem como as permissões. Esta opção não está na tela de fluxos de trabalho. Para esta opção, você precisa ir até **Conteúdo → Categorias**. Uma vez lá, abra qualquer categoria e você verá uma aba de *Fluxos de Trabalho*.

![Edição de categoria de artigos no fluxo de trabalho](../../../en/images/workflows/workflow-categories-blog.png)

### Exemplo

Certos artigos precisam estar disponíveis apenas para administradores ou usuários de uma categoria superior.

- Crie uma categoria chamada *Restrito*
- Defina todas as permissões como *Permitido* para administradores ou superiores.
- Mova os artigos em questão para a categoria *Restrito*.

Isso economiza a definição de permissões em artigos individuais.

## Controle de Versões

Quando o fluxo de trabalho está ativado, os campos geridos pelo fluxo de trabalho são excluídos do controle de versões (como "estado" e "destaque") para evitar conflitos de permissão.

## Exemplos

Alguns exemplos específicos estão disponíveis para ilustrar como usar Fluxos de Trabalho para diferentes grupos de usuários:

- [Exemplo 1](jdocmanual?article=user/workflows/workflow-example-1) utiliza os grupos de usuários padrão Autor, Editor e Publicador para preparar itens para um Boletim Informativo.
- [Exemplo 2](jdocmanual?article=user/workflows/workflow-example-2) utiliza grupos de usuários personalizados para preparar itens para reuniões de comitê.

*Traduzido por openai.com*

