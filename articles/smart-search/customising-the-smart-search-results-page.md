<!-- Filename: Customising_the_Smart_Search_results_page / Display title: Substituições de Layout da Pesquisa Inteligente  -->

## Páginas de Resultados

O componente de Pesquisa Inteligente possui cinco arquivos de layout que você pode substituir para produzir um layout ao seu gosto. Para iniciar o processo a partir do menu do Administrador:

* Selecione **Sistema / Modelos de Sites / Detalhes e Arquivos Cassiopeia**.
* Selecione a aba **Criar Substituições**.
* No painel de Componentes, selecione **com_finder**.
* Selecione o item **Search**.
* No painel do Editor, selecione **html / com_finder / search** para ver a lista de arquivos de substituição criados.

Esses arquivos não serão afetados por atualizações do Joomla, mas você pode ser lembrado de verificá-los se as fontes originais forem atualizadas.

## A Visualização de Pesquisa (Layout Padrão)

A visualização de pesquisa do layout padrão é dividida em várias partes: o layout padrão, o layout do formulário, o layout dos resultados e o layout de ordenação.

### O layout padrão (default.php)

Este layout é muito simples. Ele apenas define a estrutura na qual o formulário de pesquisa e os resultados da pesquisa são exibidos. Este layout também é responsável por carregar a folha de estilo CSS padrão para a Pesquisa Inteligente, que está localizada em `media/com_finder/css/finder.css`, então você pode querer alterá-la para carregar suas próprias regras de CSS para a Pesquisa Inteligente.

### O layout do formulário (default_form.php)

Este layout define o código necessário para que o formulário de pesquisa funcione corretamente. O layout utiliza código JavaScript, então é preciso ter cuidado para preservar seletores que não devem ser alterados, a menos que você saiba o que está fazendo.

O método de visualização `getFields` inclui vários campos ocultos que são necessários para uma pesquisa confiável. O termo de pesquisa é definido pelo campo de entrada com o nome "q".

### O layout dos resultados (default_results.php)

Este layout produz a lista de resultados correspondentes ao termo de pesquisa. Ele também gerencia a paginação e carrega um layout para cada resultado individual da pesquisa.

### O layout do resultado (default_result.php)

Este é o layout carregado para exibir um único resultado.

### O layout de ordenação (default_sorting.php)

Este item somente está presente se Mostrar Campos de Ordenação estiver definido como Sim e um ou mais Campos de Ordenação Adicionais forem selecionados na aba Avançado do Item de Menu.

*Traduzido por openai.com*

