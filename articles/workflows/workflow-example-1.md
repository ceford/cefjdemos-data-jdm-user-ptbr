<!-- Filename: J6.x:Workflow_Scenarios_Example_1 / Display title: Exemplo de Fluxo de Trabalho 1  -->

## Introdução

Um fluxo de trabalho consiste em *estágios* e *transições* entre esses estágios. Para qualquer artigo, é o estágio atual que é registrado no banco de dados e usado para identificar o fluxo de trabalho e as transições usadas por esse fluxo de trabalho.

Um único site pode ter muitos fluxos de trabalho. Aqui, um *Fluxo de Trabalho de Newsletter* é usado como exemplo para explicar como três indivíduos com diferentes funções podem estar envolvidos na produção de um artigo de newsletter. O exemplo usa os grupos de usuários Autor, Editor e Publicador padrão do Joomla. Isso tem um problema: um Autor só pode ver artigos Publicados, portanto, não pode reeditar artigos Não Publicados. Um método para evitar esse problema é abordado no [Exemplo 2](jdocmanual?article=user/workflows/workflow-example-2).

![Lista de Fluxos de Trabalho](../../../en/images/workflows/example-1-workflows-list.png)

Observe que o *Fluxo de Trabalho Básico* está definido como *Padrão*. Isso pode ter consequências problemáticas abordadas mais adiante neste artigo!

## Os Usuários

- *Arthur* é um usuário atribuído ao **Grupo de Autores** do Joomla. Ele pode criar novos artigos e editar seus próprios artigos, mas não pode editar artigos escritos por outros usuários nem mudar o estado dos artigos. Portanto, ele não pode publicar seus próprios artigos. Sua função é rascunhar novos artigos.
- *Eddie* é um usuário atribuído ao **Grupo de Editores** do Joomla. Ele pode editar artigos criados por qualquer outro usuário, incluindo Arthur e ele mesmo. Ele também não pode mudar o estado de um artigo. Sua função é revisar os artigos enviados por Eddie, verificar a precisão, ortografia e gramática, qualidade das imagens, entre outros.
- *Pru* é uma usuária atribuída ao **Grupo de Publicadores** do Joomla. Ela pode fazer tudo o que Eddie e Arthur podem fazer. Além disso, ela pode mudar o estado de um artigo. É responsabilidade dela decidir se um artigo é aceitável para publicação e publicá-lo.

## As Etapas

Existem quatro etapas neste Fluxo de Trabalho:

![Lista de Fluxos de Trabalho](../../../en/images/workflows/example-1-workflow-stages.png)

- **Rascunho** é a etapa criada por Arthur para um novo artigo.
- **Revisão** é a etapa onde Eddie assume para revisar o conteúdo.
- **Aprovar** é a etapa onde Pru decide se o artigo é bom o suficiente para ser publicado.
- **Publicar** é a etapa em que o artigo foi aprovado e publicado.

Os formulários de entrada de dados das etapas precisam de pouca explicação, apenas um Nome e uma Descrição.

## As Transições

Duas transições são necessárias entre cada etapa: uma para reverter a etapa se mais trabalho for necessário na etapa anterior; e uma segunda para migrar para a próxima etapa. Transições extras são necessárias para lidar com a extinção de um artigo:

![Lista de Fluxos de Trabalho](../../../en/images/workflows/example-1-workflow-transitions.png)

- **Rascunho/Revisão** para mover a etapa de Rascunho para Revisão.
- **Revisão/Rascunho** para reverter a etapa de Revisão para Rascunho.
- **Revisão/Aprovar** para mover a etapa de Aprovação para Revisão.
- **Aprovar/Revisão** para reverter a etapa de Aprovação para Revisão.
- **Revisão/Publicar** para mover a etapa para Publicado e mudar o status do artigo para *Publicado*.
- **Publicar** para definir o estado do artigo como *Publicado* quando a transição é executada por um Autor ou Editor.
- **Despublicar** para mudar o status do artigo para *Despublicado*.
- **Arquivar** para mudar o status do artigo para *Arquivado*.
- **Lixeira** para mudar o status do artigo para *Descartado*.

As últimas três transições permitem que Pru mude o status de um artigo quando não é mais necessário. 

### Editar Transição

O formulário de entrada de dados possui quatro abas começando com a aba *Transição*:

![Lista de Fluxos de Trabalho](../../../en/images/workflows/example-1-edit-transition.png)

- **Nome** É melhor usar as etapas Atual e Alvo no nome.
- **Etapa Atual** A etapa antes de a transição ocorrer.
- **Etapa Alvo** A etapa após a transição ocorrer.
- **Nota** Qualquer nota explicativa para ajudar a esclarecer a transição.

#### A aba *Ações de Transição*:

![Lista de Fluxos de Trabalho](../../../en/images/workflows/example-1-edit-transition-actions.png)

- **Estado de Destaque** Definir o estado de destaque que um item deve ter após executar esta transição. Deixe em *-Não Selecionado-* se o usuário que provavelmente executará esta transição não tiver permissão para destacar artigos.
- **Estado de Publicação** Definir o estado de publicação que um item deve ter após executar esta transição. Deixe em *-Não Selecionado-* se o usuário que provavelmente executará esta transição não tiver permissão para alterar o estado do artigo.

#### A aba *Notificações*:

![Lista de Fluxos de Trabalho](../../../en/images/workflows/example-1-edit-transition-notification.png)

- **Enviar Notificação** Defina como *Sim* onde notificações são necessárias, por exemplo, quando Arthur precisa notificar Eddie que um artigo está pronto para revisão.
- **Texto Adicional da Mensagem** Este é um texto adicional genérico para ajudar o destinatário.
- **Grupos de Usuários** Você pode escolher enviar a notificação para um ou mais grupos de usuários ou para nenhum e enviar a notificação para indivíduos.
- **Usuários** Selecione usuários individuais da lista de usuários.

#### A aba *Permissões*:

Note que o *Autor* tem *Executar Transição* definido como Permitido (Herdado). Não altere essas configurações para outras transições que um Autor não deve usar, pois isso também afetará Editores e Publicadores.

## A Categoria do Artigo

Cada artigo é atribuído a um fluxo de trabalho na primeira vez que é salvo. Se o artigo for inicialmente atribuído a uma Categoria que tenha um Fluxo de Trabalho selecionado, ele será atribuído a esse fluxo de trabalho. Caso contrário, ele é atribuído ao fluxo de trabalho padrão. Isso pode ser problemático porque o componente de Fluxo de Trabalho não fornece um método para alterar o fluxo de trabalho após ser alocado. Ele pode ser alterado por um Superusuário usando a Ação em Lote na página de lista de Artigos.

### Criar uma Categoria de Newsletter

É necessária uma nova categoria de Newsletter para exibir a Newsletter como um Blog de Categoria e garantir que os artigos da Newsletter sejam atribuídos ao Fluxo de Trabalho da Newsletter.

![Lista de fluxos de trabalho](../../../en/images/workflows/example-1-newsletter-category.png)

## O Item de Menu do Boletim Informativo

Para que os visitantes do site vejam o Boletim Informativo, ele precisa ser a página inicial ou estar vinculado a um item de menu. Para seguir este exemplo, crie um novo item de menu do tipo *Blog de Categoria* usando a categoria *Boletim Informativo*.

Experimente o item de menu do site. É provável que seja uma página em branco com esta mensagem:

<div class="alert alert-info">
Não há artigos nesta categoria. Se subcategorias forem exibidas nesta página, elas podem conter artigos.
</div>

## Fazer login como Arthur

Lembra-se do Arthur, o Autor? Após o login, a página do Boletim Informativo deve ter um botão rotulado como **Novo Artigo**. Selecione-o para compor um novo artigo.

### Compor um Artigo

Preencha o formulário de edição do artigo como faria para qualquer artigo. Exceto, antes de salvar pela primeira vez, dê uma olhada na aba *Publicação*.

- **Fase do Fluxo de Trabalho** deve ser definida como **Executar Transição** *Rascunho/Revisão*.
- **Categoria** deve ser configurada como *Boletim Informativo*.

Quando terminar de editar o artigo, selecione *Salvar* ou *Salvar & Fechar*.

<div class="alert alert-danger">Após fechar o artigo, Arthur não poderá editá-lo novamente porque os usuários no grupo de Autor não podem visualizar artigos Não Publicados.</div>

## Fazer login como Eddie

Eddie, o Editor, tem permissão para visualizar artigos não publicados, então a página do Boletim Informativo mostra quaisquer itens não publicados para ele editar.

### Revisar o Artigo

Selecione o artigo redigido por Eddie e faça as alterações necessárias para melhorá-lo. Quando estiver satisfeito, na *Aba de Publicação*:

- O **Estágio do Fluxo de Trabalho** deve ser definido como **Executar Transição** *Revisar/Aprovar*.

Diferente de Arthur, que não pode ver seu artigo após salvá-lo, Eddie pode ver e editar o artigo novamente. Ele também pode definir a transição para a próxima etapa para Aprovar/Publicar. A transição funcionará, mas o artigo não será publicado, pois Eddie não tem permissão para Publicar.

## Fazer login como Pru

Quando a etapa de Aprovação foi definida no fluxo de trabalho, Pru deveria ter recebido uma mensagem solicitando uma ação. Então, faça login como Pru para revisar o artigo e definir sua Etapa do Fluxo de Trabalho para **Executar Transição** *Publicar*. *Salve e feche* o artigo para ver o resultado publicado. Faça logout para ver o resultado sem o link de Edição.

Reflexão: outra etapa é necessária para permitir que Pru reverta a etapa de Publicar para Revisar caso ela queira que Eddie corrija algo.

## Fluxo de Trabalho do Backend

Os grupos de usuários Autor, Editor e Publicador são destinados ao uso no frontend. O problema para o Arthur é que ele não pode acessar seus artigos em rascunho a partir do frontend porque seu grupo de usuário não tem permissão de visualização para artigos não publicados.

Você pode permitir o acesso ao backend para todos os membros desses grupos da seguinte forma:

- Vá para a página de **Configuração Global**.
- Selecione a aba **Permissões**.
- Selecione *Autor* e defina **Login de Administrador** como *Permitido*.
- **Salvar**
- Vá para a página **Artigos: Opções**.
- Selecione sua aba **Permissões**.
- Selecione *Autor* e defina **Acessar Interface de Administração** como *Permitido*.

Isso permitirá que Arthur, Eddie e Pru façam login no backend com acesso aos itens de Conteúdo. Um Painel Inicial muito reduzido:

![Painel inicial para Arthur](../../../en/images/workflows/example-1-backend-home.png)

Mas Arthur tem acesso aos seus artigos em rascunho:

![Lista de artigos para Arthur](../../../en/images/workflows/example-1-backend-articles.png)

Observe que Arthur não pode editar o último item na lista porque não é um de seus próprios artigos. O título do artigo não está vinculado. Da mesma forma, Arthur não pode editar nenhuma das categorias existentes porque ele não tem permissão e elas também não estão vinculadas. Ele pode criar uma nova Categoria, mas ela fica Não Publicada e ele não pode publicá-la!

## Correção para Fluxo de Trabalho Errado

Se você atribuir um artigo ao fluxo de trabalho errado, há dois métodos disponíveis para corrigir o problema.

### Método de Super Usuário

- Vá para a lista de **Artigos**.
- Selecione a caixa de seleção para o artigo com problema.
- Selecione o botão **Ações** na Barra de Ferramentas.
- Selecione o botão **Lote** na lista.
- Selecione **Alterar Etapa** no diálogo *Processar Lote de Artigos Selecionados*.
- Selecione um Fluxo de Trabalho e Etapa apropriados como destino.
- Selecione o botão **Processar**.

![Lista de artigos para Arthur](../../../en/images/workflows/example-1-backend-batch.png)

### Método Alternativo

Alternativamente, você pode editar uma tabela de banco de dados com phpMyAdmin ou similar.

Informação necessária:

- O ID do artigo na última coluna da lista de Artigos.
- O ID de uma etapa no fluxo de trabalho desejado na última coluna da lista de
  Etapas do Fluxo de Trabalho que você gostaria de usar.

No phpMyAdmin:

- Pesquise na tabela #__workflow_associations para encontrar o item_id que contém
  o ID do seu artigo.
- Altere o valor stage_id para o ID da etapa que você encontrou no fluxo de trabalho desejado.

Volte à sua lista de artigos e verifique se o item com problema agora está usando
o fluxo de trabalho correto.

*Traduzido por openai.com*

