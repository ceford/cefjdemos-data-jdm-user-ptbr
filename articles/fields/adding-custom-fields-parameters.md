<!-- Filename: J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields / Display title: Parâmetros do Campo -->

## Formulário de Entrada de Dados de Campo

Existem 16 ou mais tipos de campo disponíveis na lista de seleção de Tipo no formulário de entrada de dados de campo. A maioria dos campos do formulário é igual para todos os tipos de campo, mas outros mudam conforme o tipo selecionado. Este artigo descreve os parâmetros comuns para todos os campos. O formulário de entrada de dados também é o mesmo para os campos de **Artigo**, **Contato** e **Usuário** e seus campos de Categoria.

Uma lista de Campos estará vazia inicialmente. Para começar, por exemplo, com campos de Artigo:
* Selecione **Novo** na Barra de Ferramentas na lista de Campos: Artigos.

O formulário consiste em um campo de Título e quatro abas.

![Aba geral de parâmetros do campo](../../../en/images/fields/fields-parameters-general-tab.png)

## Título

O título é exibido na página de lista *Artigos: Campos*, onde pode ser
selecionado para abrir o campo para edição. O título não é exibido quando você
cria um artigo ou no frontend. No entanto, o Rótulo pode ser criado a partir
do Título e é exibido no formulário de entrada de dados do Artigo e
pode ser exibido na exibição do Artigo.

### Aba Geral

#### No painel esquerdo:

- **Tipo** Selecione um dos 16 tipos de campos da lista suspensa. Quando
você salva o campo, esse tipo é permanente. Você não pode alterá-lo
mais tarde.
- **Nome** O nome será usado para identificar o campo. Deixe em branco e
o Joomla preencherá com um valor padrão a partir do título.
- **Rótulo** Use um rótulo descritivo para o campo. Este texto não é
traduzível. Se você não inserir nenhum texto para um rótulo, o texto do 
título será usado como rótulo.
- **Descrição** Texto que será mostrado como uma dica de ferramenta para descrever
o propósito do campo durante a entrada de dados. Este texto não é traduzível e
não será exibido no frontend.
- **Obrigatório** Defina como *Sim* se este for um campo obrigatório que deve
ser preenchido antes de enviar um artigo.
- **Usar Apenas em Subformulário** Explicação necessária [A Fazer]
- **Valor Padrão** Defina um valor padrão, se apropriado. Este texto não é
traduzível.
- **Filtro** Escolha uma das opções disponíveis na lista suspensa. O
campo será validado para conformidade com o tipo de dado selecionado.
- **Comprimento Máximo** Defina isso para limitar o comprimento dos dados de texto que podem ser
inseridos.

### No painel direito:

- **Status** Defina um estado de publicação selecionado de *Publicado*, *Não Publicado*,
*Arquivado* ou *Lixeira*.
  - Publicado: O campo é visível ao editar um artigo ou um
    contato. E é visível no Frontend.
  - Não Publicado: O campo não será visível para os usuários ao editar
    um artigo ou um contato.
  - Arquivado: O campo não será mais exibido na edição de um artigo ou um
    contato. Você pode abri-lo no gerenciador de campos quando definir o
    filtro para arquivado.
  - Lixeira: O campo é deletado, mas ainda está no banco de dados. Ele pode ser
    permanentemente excluído do banco de dados com a função Esvaziar Lixeira
    no Gerenciador de Campos.
- **Grupo de Campos** Selecione Nenhum ou um Grupo selecionado a partir de uma lista predefinida. Grupos
aparecem como guias separadas no formulário de entrada de dados do Artigo.
- **Categoria** Você pode atribuir um campo a uma ou mais categorias de campo. Note
  que o padrão *Todos* não inclui artigos *não categorizados*.
- **Acesso** O Nível de Acesso de visualização para este campo.
- **Idioma** Selecione o idioma para este campo personalizado. Se você não estiver usando o
  recurso de multi-idioma do Joomla, mantenha o padrão como *Todos*.
- **Nota** Um campo opcional para fazer suas anotações pessoais para o campo.

### Aba Opções

![Parâmetros do campo aba opções](../../../en/images/fields/fields-parameters-options-tab.png)

#### Opções de Formulário

- **Texto de Placeholder** Um texto de placeholder que aparecerá dentro do campo personalizado
como dica para a entrada. O placeholder está ativo no Backend enquanto
se cria um artigo. Você não o vê no Frontend.
- **Classe do Campo** Os atributos de classe do campo quando o campo é renderizado.
Se classes diferentes forem necessárias, liste-as com espaços.
- **Classe do Rótulo (Formulário)** Os atributos de classe do campo no formulário de edição. Se
classes diferentes forem necessárias, liste-as com espaços.
- **Editável Em** Em qual parte do site o campo deve ser exibido: Site,
Administrador ou Ambos.
- **Atributo Exibir em** Mostrar ou ocultar condicionalmente o campo dependendo do
valor de outros campos. A sintaxe a ser usada aqui, por exemplo:
  - `lista-de-itens:valor1[OU]lista-de-itens:valor2` onde
  - lista-de-itens: O nome de um campo já criado do qual este campo
depende.
  - valor1: O valor necessário no campo de lista de itens para que este campo seja exibido.
  - [OU] Para criar uma escolha entre múltiplos campos. No exemplo, este campo será
exibido quando o campo lista-de-itens tiver um valor de valor1 OU valor2.
  - [E] Para combinar múltiplos campos. Este campo será exibido somente quando os
campos lista-de-itens tiverem o valor valor1 E valor2.
  - Você também pode usar valor 'diferente de' como em lista-de-itens!:valor1. A
sintaxe mostrará este campo somente quando lista-de-itens não for igual a valor1
  - Para mostrar este campo quando o campo lista-de-itens tiver sido selecionado e não
tiver um valor vazio, use a sintaxe lista-de-itens!: (sem um valor especificado).
  - Nota: Campos de subformulário tratam o nome lista-de-itens de maneira diferente.
Se você criar um campo de Subformulário e adicionar este campo condicional para um campo
que você está criando lá, você precisará usar field[ID] em vez de lista-de-itens,
onde ID é o id do campo lista-de-itens. Portanto, o atributo exibir em
para este campo condicional que você está criando precisa ser:
field36:valor1[OU]field36:valor2 onde 36 é o ID do campo 'Lista de itens'.
Isso precisa de esclarecimento!

#### Opções de Exibição

- **Classe de Exibição** A classe do contêiner do campo na saída.
- **Classe do Valor** A classe do valor do campo na saída.
- **Rótulo** Mostrar ou ocultar o rótulo.
- **Classe do Rótulo (Saída)** A classe de saída do rótulo se o rótulo for exibido.
- **Exibição Automática** O Joomla oferece alguns eventos de conteúdo que são acionados
durante o processo de criação de conteúdo. Este é o lugar para definir como os campos personalizados
devem ser integrados ao conteúdo. Você pode escolher *Depois do Título*,
*Antes de Exibir o Conteúdo*, *Depois de Exibir o Conteúdo* ou *Não exibir automaticamente*.
- **Prefixo** Texto fixo a ser exibido antes de um campo, por exemplo, £.
- **Sufixo** Texto fixo a ser exibido após um campo, por exemplo, EUR.
- **Layout** Selecione um layout a partir dos modelos e sobreposições disponíveis.
- **Exibir Quando Somente Leitura** Selecione entre *Herdar*, *Sim* ou *Não*. Se o campo for
somente leitura (talvez o usuário não tenha o nível de acesso), o campo deve ser
exibido ou oculto.

#### Pesquisa Inteligente

- **Índice de Pesquisa** Selecione a partir de uma lista de opções. Aviso: Quando *Fazer pesquisável*
é selecionado, o conteúdo do campo é indexado com as permissões de visualização do
item de conteúdo. Isso pode levar à divulgação inesperada de informações.

### Aba Publicação

![Parâmetros do campo aba publicação](../../../en/images/fields/fields-parameters-publishing-tab.png)

### Aba Permissões

As permissões para cada grupo de usuários são autoexplicativas para as ações *Excluir*, *Editar* e *Editar estado*. As permissões indicam quem pode fazer o quê com o campo como um todo — por exemplo, excluí-lo, modificá-lo ou despublicá-lo.

![Parâmetros do campo aba permissões](../../../en/images/fields/fields-parameters-permissions-tab.png)

A permissão *Editar valor de campo personalizado* pode causar confusão. Ela define quem pode alterar o conteúdo do campo. Por padrão, essa permissão está configurada como **Não permitido (Herdado)** para todos os grupos, exceto para Superusuários. Dois exemplos:

* **Dados personalizados de registro de usuário**
  Suponha que você crie um campo de usuário para *Gênero*, a ser adicionado a um formulário de registro. Esse campo pode ser uma lista ou botão de opção (radio button) para que o usuário selecione *Masculino* ou *Feminino*. Nesse caso, a permissão para o grupo Público deve ser definida como *Permitido*. Caso contrário, um usuário visitante não conseguirá selecionar um gênero. Como todos os outros grupos herdam do grupo Público, um usuário registrado poderá alterar a seleção de gênero no perfil após fazer login.
* **Comentário em artigo**
  Suponha que você queira permitir que um Autor adicione um comentário a um artigo. Isso pode ser um campo de texto com comprimento limitado. Nesse caso, a permissão para o grupo Autor deve ser definida como *Permitido*. Os grupos Editor e Publicador herdarão essa configuração quando o formulário for salvo. Os grupos Gerente e Administrador têm permissão para editar artigos, mas não para editar valores de campos personalizados — a menos que a permissão para o grupo Gerente também seja definida como *Permitido*.

*Traduzido por openai.com*

