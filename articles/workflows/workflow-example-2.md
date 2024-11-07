<!-- Filename: J6.x:Workflow_Scenarios_Example_2 / Display title: Exemplo de Fluxo de Trabalho 2  -->

## Introdução

Este exemplo envolve dois usuários, Alice e Bob, que são respectivamente a presidente e o secretário de um comitê. O fluxo de trabalho envolve a preparação e aprovação de agendas e atas das reuniões do comitê. Charlie é um membro do comitê que terá acesso aos documentos do comitê quando forem publicados. O fluxo de trabalho usa apenas o frontend.

## Grupos de Usuários

Primeiro crie novos Grupos de Usuários, todos filhos de *Registrado*.

- **Comitê** Um filho de *Registrado* 
- **Presidente** Um filho de *Comitê*
- **Secretário** Um filho de *Comitê*

![Grupos de usuários personalizados](../../../en/images/workflows/example-2-user-groups.png)

## Nível de Acesso do Usuário

- Crie um novo nível, **Comitê** e adicione *Comitê* aos Grupos de Usuários Com Acesso de Visualização.
- No Nível de Acesso *Especial*, adicione *Comitê* aos Grupos de Usuários Com Acesso de Visualização.

![Níveis de Acesso de Visualização](../../../en/images/workflows/example-2-viewing-access-levels.png)

## Criar Usuários

- **Alice** no grupo *Presidente*.
- **Bob** no grupo *Secretário*.
- **Charlie** no grupo *Comitê*.

## Criar o Fluxo de Trabalho

- **Nome** *Fluxo de Trabalho do Comitê*
- **Descrição** *Fluxo de trabalho para preparação de documentos do Comitê.*
- **Permissões**
  - **Comitê** Todos definidos como *Herdados* Não permitido (herdado).
  - **Presidente** Todos definidos como *Permitido* exceto *Excluir*. Talvez...
  - **Secretário** Todos definidos como *Permitido* exceto *Excluir* e *Editar Estado*.

![Lista de fluxos de trabalho](../../../en/images/workflows/example-2-workflows-list.png)

### Criar as Etapas do Fluxo de Trabalho

- **Rascunho** 
  - **Nota** *Documentos em preparação.* 
  - **Permissões** Todos deixados como *Herdados*.
- **Revisão**
  - **Nota** *Documentos aguardando aprovação.* 
  - **Permissões** Todos deixados como *Herdados*.
- **Publicação**
  - **Nota** *Documentos publicados.* 
  - **Permissões** Todos deixados como *Herdados*.

![Etapas do fluxo de trabalho](../../../en/images/workflows/example-2-stages-committee-workflow.png)

### Criar as Transições do Fluxo de Trabalho

#### Rascunho para Revisão

Esta é a transição normal para frente na sequência de etapas.

- **Nome** *Rascunho/Revisão*
- **Aba de Transição**
  - **Estágio Atual** *Rascunho*
  - **Estágio Alvo** *Revisão*
  - **Nota** *Transição para próxima etapa.*
- **Ações de Transição**
  - **Estado de Exposição** *- Nenhum Selecionado -*
  - **Estado de Publicação** *- Nenhum Selecionado -*
- **Aba de Notificação**
  - **Enviar Notificação** *Sim* Destinatários precisam de *Receber Emails do Sistema* habilitado para receber notificações por email.
  - **Texto Adicional da Mensagem** Algo específico para este fluxo de trabalho?
  - **Grupos de Usuários** *Presidente*
  - **Usuários** Uma alternativa ao uso de Grupos de Usuários.
- **Aba de Permissões** Todos definidos como **Herdados**.

#### Revisão para Rascunho

Esta é a reversão para uma etapa anterior na sequência, invocada quando o Presidente requer mais trabalho do Secretário. Os campos do formulário são semelhantes aos campos de Rascunho/Revisão, exceto pela Nota e os *Estágios Atual* e *Alvo* que são invertidos.

#### Revisão para Publicação

Esta é a transição que muda o estado de um item de *Não Publicado* para *Publicado*. Apenas o Presidente tem permissão para fazer essa mudança.

- **Nome** *Revisão/Publicação*
- **Aba de Transição**
  - **Estágio Atual** *Revisão*
  - **Estágio Alvo** *Publicação*
  - **Nota** *A transição final para publicação.*
- **Ações de Transição**
  - **Estado de Exposição** *- Nenhum Selecionado -*
  - **Estado de Publicação** *Publicado*
- **Aba de Notificação**
  - **Enviar Notificação** *Sim* Destinatários precisam de *Receber Emails do Sistema* habilitado para receber notificações por email.
  - **Texto Adicional da Mensagem** *Um documento do comitê foi publicado e agora está disponível para visualização.*
  - **Grupos de Usuários** *Comitê*
  - **Usuários** Uma alternativa ao uso de Grupos de Usuários.
- **Aba de Permissões**
  - **Secretário** Definir *Executar Transição* como *Negado*.

#### Publicar para Revisão

Esta é uma mudança de Publicação de volta para Revisão. É realmente necessário? Um artigo publicado ainda pode ser editado pelo Secretário ou Presidente. Talvez um documento do Comitê com dados sensíveis tenha sido publicado por engano.

Se necessário, crie uma Transição semelhante à transição *Revisão para Publicação* mas com as Etapas invertidas, as *Ações de Transição / Estado de Publicação* definidas para *Não Publicado* e uma mensagem genérica em *Texto Adicional da Mensagem*.

#### Arquivar

Esta é a transição executada quando um documento do Comitê não é mais necessário. No fluxo de trabalho, ele permanece no estágio de Publicação, mas o Estado do artigo é alterado de Publicado para Arquivado.

- **Nome** *Arquivo*
- **Aba de Transição**
  - **Estágio Atual** *Publicação*
  - **Estágio Alvo** *Publicação*
  - **Nota** *Alterar o estado do item de Publicado para Arquivado.*
- **Ações de Transição**
  - **Estado de Exposição** *- Nenhum Selecionado -*
  - **Estado de Publicação** *Arquivado*
- **Aba de Notificação**
  - **Enviar Notificação** *Não* Esta não é uma transição que requer ação. 
- **Aba de Permissões**
  - **Secretário** Definir *Executar Transição* como *Negado*.

![Transições do fluxo de trabalho](../../../en/images/workflows/example-2-transitions-committee-workflow.png)

## Criar uma Nova Categoria

<div class="alert alert-warning">Este passo é realmente importante! Novos 
documentos do Comitê devem ser criados com esta categoria, caso contrário, 
eles seguirão o fluxo de trabalho padrão que precisa de um Super Usuário para alterar.</div>

- **Título** *Comitê* 
- **Fluxo de Trabalho** Selecione *Fluxo de Trabalho do Comitê* na lista de Fluxos de Trabalho.
- **Permissões** 
  - Autor, Editor e Publicador: Tudo configurado como *Não Permitido* ou 
    deixado como *Não Permitido (Herdado)*.
  - Comitê: Tudo deixado como *Herdado*.
  - Presidente: Todos, exceto *Excluir*, configurados como *Permitido*.
  - Secretário: Todos, exceto *Excluir* e *Editar Estado*, configurados como 
    *Permitido*.

## Criar um Item de Menu

- **Título** *Documentos do Comitê*
- **Tipo de Item de Menu** Lista de Categorias
- **Escolher uma Categoria** *Comitê*
- **Acesso** *Comitê*

![Item de menu de documentos do comitê](../../../en/images/workflows/example-2-menu-item.png)

## Verifique o Site

Faça login como Alice, Bob, Charlie e um Superusuário, cada um por vez, para ver o que eles podem ver:

Alice, Bob e Charlie podem ver o item do Menu, mas ninguém mais pode, nem mesmo um Superusuário. Após selecionar o item do menu, Alice e Bob podem ver uma tabela de Documentos do Comitê, incluindo os que não foram publicados. Charlie pode ver apenas uma tabela de Documentos do Comitê que foram publicados ou uma mensagem explicativa se nenhum tiver sido publicado.

Alice e Bob também podem ver um link de Editar para cada artigo e um botão **Novo Artigo**. Este botão é geralmente usado por Bob para criar um Documento do Comitê, mas Alice também pode fazê-lo.

![Visão de Bob da página da lista de categorias dos documentos do comitê](../../../en/images/workflows/example-2-committee-papers.png)

### Para Criar e Publicar um Documento do Comitê

- Faça login como Secretário e selecione o botão **Novo Artigo** na página de 
  *Documentos do Comitê*.
- Insira o texto e *Salve*. Isso pode ser feito ao longo de várias sessões de edição, talvez ao longo de vários dias ou semanas. O artigo permanece Não Publicado e na fase de Rascunho até...
- Selecione a aba *Publicação* no formulário de edição e defina o *Estágio do Fluxo de Trabalho* para Executar Transição **Rascunho/Revisão**. 
- Selecione **Salvar & Fechar** para executar a transição.
- O trabalho do Secretário está completo por enquanto e uma mensagem foi enviada ao Presidente do Comitê.
- O Presidente faz login, verifica o documento pronto para Revisão e usa a transição **Revisar/Publicar** para tornar o documento *Publicado*. O trabalho do Presidente está completo por enquanto e uma mensagem é enviada aos membros do Comitê.
- Os membros do Comitê podem fazer login e acessar o documento publicado.

*Traduzido por openai.com*  

