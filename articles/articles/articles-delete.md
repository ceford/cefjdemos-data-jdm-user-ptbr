<!-- Filename: J4.x:Deleting_an_Article / Display title: Artigos: Excluir -->

## Introdução

No Joomla, a exclusão de um artigo é um processo de duas etapas. A primeira etapa envia o artigo para a *Lixeira*, de onde ele pode ser restaurado. A segunda etapa o exclui da Lixeira, após o que o artigo é removido permanentemente.

## Considerações

Considere por que você quer deletar o artigo:

- Ele não é mais necessário? Se for o caso, a exclusão é provavelmente a
  ação correta a ser tomada.
- É um artigo que poderia ser reutilizado no futuro? Pode ser muito
  frustrante saber que você tinha um artigo que teria sido um bom ponto
  de partida para outro, mas você o deletou - considere arquivá-lo
  em vez disso.

## Movendo o Artigo para a Lixeira

- Selecione **Conteúdo -> Artigos** no menu do Administrador.
- Marque a caixa de seleção para selecionar o artigo que você deseja excluir. Um artigo **deve** ser selecionado para ativar o botão **Ações** na barra de ferramentas.
- Selecione o botão **Ações** na Barra de Ferramentas.
- Selecione **Lixeira** no menu suspenso.

![Artigo selecionado para exclusão](../../../en/images/articles/articles-selected-to-trash.png)

Haverá uma mensagem de confirmação e o artigo terá desaparecido da lista atual de artigos, uma vez que normalmente não inclui itens na lixeira.

## Filtrar para Restaurar ou Excluir

Nesta etapa do processo, o artigo não foi removido completamente. Este é um recurso útil caso você tenha excluído o artigo por engano.

Para ver a lista de artigos na lixeira:

- Selecione o botão **Opções de Filtro** para abrir a lista de filtros.
- Selecione **Na Lixeira** na lista *-- Selecionar Status --*.

![Visualização da lixeira de artigos](../../../en/images/articles/articles-trash-list.png)

### Para Restaurar

Se você mudou de ideia, pode selecionar o símbolo **Na Lixeira** na coluna *Status*. O artigo voltará ao estado *Publicado* e desaparecerá da lista de artigos na lixeira.

### Para Excluir

Selecione a caixa de seleção na coluna esquerda dos dados do artigo. Isso ativará os botões *Ações* e *Excluir* na Barra de Ferramentas. O botão *Ações* permite aplicar a mesma ação a todos os artigos selecionados. Se você realmente tem certeza:

1. Selecione o botão *Excluir* na Barra de Ferramentas. Uma caixa de mensagem aparecerá:<br>
    <div class="alert alert-light">
    Tem certeza de que deseja excluir? Confirmar irá excluir permanentemente o(s) item(ns) selecionado(s)!</div>
2. Selecione **OK** para confirmar e o artigo será excluído da Lixeira. O artigo será excluído do banco de dados. Ele se foi, permanentemente!
3. Selecione o botão **Limpar** ao lado de **Opções de Filtro** para retornar à lista de **Artigos** sem filtro.

## Dicas

- Lembre-se, excluir um artigo não é o mesmo que arquivar um artigo. Uma vez que ele for excluído da Lixeira, ele se foi para sempre.
- Se você excluir um artigo por engano, mas não o excluir da Lixeira, você pode alterar seu status. Você tem as opções de defini-lo como *Arquivado*, *Publicado* ou *Não Publicado*.
- O Joomla não permite que você salve mais de um artigo com o mesmo alias. Se um artigo é excluído, mas permanece na Lixeira, ele ainda existe. Se você tentar salvar um artigo e receber um erro informando que o alias já existe, ele pode estar na Lixeira! Portanto, você deve esvaziar a lixeira ou pode inserir um alias diferente para seu novo artigo.
- O Joomla mantém versões anteriores de um artigo, a menos que Versiones esteja desativado. Se você estiver excluindo um artigo porque ele de alguma forma "quebrou", tente reverter para uma versão anterior.

*Traduzido por openai.com*

