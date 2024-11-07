<!-- Filename: Help4.x:Components_Version_History / Display title: Artigo: Versões  -->

## Introdução

No formulário de edição de artigos do Joomla, cada vez que um artigo é salvo, uma nova versão é criada automaticamente. O número de versões a manter para cada artigo pode ser configurado na página *Artigos: Opções*, aba *Layout de Edição*. O padrão é 10. Note que esta não é a aba *Opções* da página *Artigos: Editar*. A versão atual é geralmente a última versão salva.

Uma ou mais versões podem ser marcadas para *Manter para Sempre*. Essas versões não serão excluídas automaticamente, mesmo que o número máximo de versões seja excedido.

O diálogo pop-up *Versões* é usado para gerenciar versões anteriores do item que está sendo editado. Históricos de versões semelhantes estão disponíveis para Artigos, Banners e Clientes, Contatos, Feeds de Notícias, Notas de Usuário e todas as Categorias.

Nota: Campos personalizados não são armazenados em diferentes versões.

## Como Acessar

Selecione o botão **Versões** na barra de ferramentas enquanto edita o item.  

## Captura de Tela

![Caixa de diálogo de versões](../../../en/images/articles/articles-versions.png)

## Cabeçalhos de Coluna

- **Caixa de Seleção** Esta caixa de seleção é usada para selecionar ou desmarcar todas as versões visíveis na lista. Se alguma caixa de seleção estiver marcada, os botões da barra de ferramentas são ativados e podem ser usados para realizar uma ação nos itens selecionados.
- **Data** A hora e data em que a versão foi salva. Clicar neste link abre uma visualização prévia dessa versão em uma janela pop-up. Note que uma das datas será seguida por um símbolo de estrela. Isso indica que essa é a versão que está atualmente salva e sendo editada.
- **Nota da Versão** Quando você edita um item, tem a opção de inserir uma Nota da Versão. Isso pode ser usado para ajudá-lo a lembrar qual versão possui qual informação. Se você inseriu uma Nota da Versão antes de salvar o item, ela aparecerá nesta coluna.
- **Manter para Sempre** Esta coluna mostra se você marcou a versão como Manter para Sempre. Normalmente, cada versão será retida de acordo com as configurações da página de opções do componente. As configurações padrão são para manter um máximo de 10 versões anteriores de um item. Nesse caso, quando você salva um item que já possui 10 versões salvas, a versão mais antiga é excluída. Se uma versão for marcada como Manter para Sempre, não será contada como uma das versões salvas e não será excluída quando o número máximo for atingido. Para alternar o Manter para Sempre ativado ou desativado, marque a caixa de seleção da versão e depois selecione o botão *Manter Ligado/Desligado* na barra de ferramentas.
- **Autor** O usuário que salvou esta versão.
- **Contagem de Caracteres** O número total de caracteres salvos nesta versão. Isso inclui os nomes das colunas do banco de dados, assim como os caracteres do item.

## Barra de Ferramentas

No topo da página, você verá a barra de ferramentas mostrada na captura de tela acima. As funções são:

- **Restaurar** A versão atual do item está marcada com uma estrela à direita da data. Se você deseja restaurar uma das outras versões salvas, marque a caixa de seleção para a versão desejada e selecione o botão *Restaurar*. A versão atual do item será substituída pela versão selecionada, e a tela de edição será recarregada com a versão restaurada carregada no editor.
- **Pré-visualizar** Para pré-visualizar uma versão, selecione o item na coluna de Data ou marque a caixa de seleção e clique no botão Pré-visualizar. Uma janela do navegador separada será carregada mostrando a versão selecionada do item, similar à captura de tela abaixo. Após visualizar a versão, feche a janela do navegador. 
![Caixa de diálogo de pré-visualização de versões](../../../en/images/articles/articles-versions-preview.png)
- **Comparar** Para comparar duas versões e ver o que foi alterado, clique nas caixas de seleção para cada uma das versões e clique no botão Comparar. Uma nova janela do navegador será aberta, conforme mostrado na captura de tela abaixo. A primeira coluna é o nome do campo, a segunda é a versão mais antiga, a terceira é a versão mais recente, e a última coluna destaca as diferenças entre as duas versões.
![Caixa de diálogo de comparação de versões](../../../en/images/articles/articles-versions-compare.png)
- **Manter Ativado/Desativado** Este botão permite alternar a funcionalidade Manter Para Sempre de uma versão. Normalmente, a versão mais antiga de um item será excluída automaticamente quando o número máximo de versões (definido nas Opções do componente) for excedido. Se você definir a propriedade Manter Para Sempre para uma versão, ela nunca será excluída automaticamente.
- **Excluir** Este botão permite que você exclua manualmente uma ou mais versões. Selecione a caixa de seleção para as versões que deseja excluir e então selecione o botão Excluir. Note que isso *não* exclui o item que está sendo editado. Apenas exclui a versão selecionada do item.

