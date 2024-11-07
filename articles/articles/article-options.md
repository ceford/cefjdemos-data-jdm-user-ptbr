<!-- Filename: J6.x:_Article_Options / Display title: Artigo: Editar - Opções -->

## Introdução

A palavra *Opções* é ambígua no Joomla! Às vezes, é usada de forma intercambiável com *Parâmetros* e a maioria das visões de lista de componentes possui um botão *Opções* na Barra de Ferramentas. Isso leva a uma página de Opções onde os parâmetros do componente como um todo são definidos. Além disso, muitos formulários de edição de itens de componentes têm uma aba rotulada como *Opções* usada para definir os parâmetros para aquele item específico.

Este artigo é sobre a aba *Opções* no formulário *Artigo: Editar*. É onde são definidos os parâmetros que afetam a aparência geral do artigo sendo editado. As opções para artigos como um todo são abordadas em um artigo separado.

## Captura de Tela

A aba *Opções* do formulário *Artigo: Editar* possui uma série de painéis, na maioria das vezes com a escolha de *Usar Global (Ocultar ou Mostrar)*, *Ocultar* ou *Mostrar*. A captura de tela parcial a seguir mostra o layout geral.

![Aba de opções de edição de artigo](../../../en/images/articles/articles-edit-options-tab.png)

## Painel de Layout

Um artigo, ou parte dele, pode aparecer como uma única página ou em um layout de blog de categoria controlado por um item de menu. Em um item de menu de blog, a maioria dos campos de layout possui opções de *Usar Global*, *Sim/Não* ou *Mostrar/Esconder* e *Usar Configurações do Artigo*. As opções neste painel não têm efeito em layouts de blog, a menos que a opção *Usar Configurações do Artigo* seja selecionada no item de menu.

Caso contrário, essas opções afetam a aparência do artigo único que está sendo editado.

- **Layout** Na instalação padrão, as duas primeiras escolhas são oferecidas:
  - **---Das Opções Globais--- / Usar Global** Isso se refere à configuração de *Artigos: Opções* disponível no botão *Opções* na Barra de Ferramentas da visualização da lista de *Artigos*. Seu valor em *Escolher um Layout* é definido como *Padrão*.
  - **---Do Componente--- / Padrão** Isso se refere à configuração em *Artigos: Opções*. Em uma instalação padrão é efetivamente o mesmo que a opção *Usar Global*. Mas se existir uma substituição nomeada default.php, então essa substituição é usada para o layout.
  - **---Do Modelo cassiopeia--- / nome-da-sobrescrita** Se uma substituição do modelo tiver sido criada com um nome diferente de *padrão*, ela aparecerá aqui e poderá ser selecionada como um layout alternativo.
- **Título** É normal mostrar o título de um artigo, mas podem haver circunstâncias em que isso não seja apropriado. Selecione *Esconder* para omitir o título do artigo da exibição da página.
- **Títulos Vinculados** O comportamento padrão é tornar o título de um artigo um link para o próprio artigo quando ele aparece em layouts de blog ou lista. Essa configuração é controlada pelo item de menu. Pode ser configurada para *Usar Global (Sim)*, *Usar Configurações do Artigo*, *Não* ou *Sim*. Se o item de menu estiver configurado para *Usar Configurações do Artigo*, então o valor de *Títulos Vinculados* no artigo será utilizado. Caso contrário, essa configuração não tem efeito. Se o título não estiver vinculado, você poderá usar um link *Leia Mais* para acessar o artigo a partir de um layout de blog ou lista.
- **Tags** Mostrar ou Esconder as tags na página do artigo único.
- **Texto de Introdução** Mostrar ou Esconder o texto de introdução na página do artigo único. Há algumas circunstâncias em que você pode desejar ter um texto de introdução completamente diferente para layouts de blog que seja deixado de fora no texto completo do artigo.
- **Posição das Informações do Artigo** Isso se refere ao bloco de informações sobre um artigo, encabeçado por *Detalhes* e contendo as informações de *Autor*, *Categoria*, *Publicado* e *Visualizações*. O padrão é ter isso acima do texto do artigo. Configure para Abaixo para mover abaixo do texto do artigo em uma visualização de artigo único. Se configurado para *Dividir*, o item *Visualizações* será movido para abaixo do texto do artigo.
- **Título das Informações do Artigo** Mostrar ou Esconder a palavra *Detalhes* acima da lista de informações do artigo na visualização de artigo único.

## Painel de Categoria

Os campos neste painel funcionam como você poderia esperar. Nas visualizações de blog, as configurações do item de menu têm precedência, a menos que estejam definidas como *Usar Configurações do Artigo*.

- **Categoria** Mostrar ou Ocultar o nome da Categoria.
- **Link da Categoria** Vincular (Sim ou Não) o nome da Categoria. Se ajustado para *Sim*, o nome da Categoria é vinculado ao blog de sua categoria.
- **Categoria Parental** Se ajustado para Sim, a categoria parental aparece como um item separado acima da Categoria na seção de informações do artigo *Detalhes* no layout de artigo único.
- **Link da Categoria Parental** Se ajustado para Sim, o nome da Categoria Parental é vinculado à página de blog de sua categoria.

## Painel de Associações

Este painel está presente apenas em sites multilíngues.

- **Associações** Se configurado para Mostrar, um item extra é adicionado nas informações do artigo, começando com *Também disponível em:* seguido por bandeiras que representam as versões deste artigo disponíveis em outros idiomas.
- **Usar Imagens de Bandeiras** Este item aparece se *Associações* estiver configurado para *Mostrar*. O padrão *Sim* exibe botões como bandeiras de idiomas. A alternativa *Não* exibe botões como códigos de idioma, por exemplo, *en-GB*. 

## Painel do Autor

- **Autor** Mostrar ou ocultar o nome do autor deste artigo na exibição de artigo único. A linha nas informações do artigo lê *Escrito por: Nome do Autor*
- **Link para a Página de Contato do Autor** Sim ou não para vincular o Nome do Autor à página de contato do autor, se houver uma.

## Painel de Datas

Os artigos do Joomla armazenam várias datas. Se exibidas, cada uma das seguintes aparece como linhas separadas nas informações de um único artigo. Lembre-se, os layouts de blog usam as configurações do item de menu, a menos que esteja definido para *Usar Configurações do Artigo*. O formato da data é 03 de novembro de 2024, mas isso pode ser alterado ...[A Fazer]

- **Data de Criação** Oculta por padrão.
- **Data de Modificação** Oculta por padrão.
- **Data de Publicação** Exibida por padrão.

## Painel de Opções

- **Navegação** Para um artigo que faz parte de uma série de artigos em uma categoria, há botões de *Anterior* e *Próximo* abaixo do texto do artigo para navegar para as páginas anteriores ou seguintes. Se configurado para *Ocultar*, os botões de navegação não serão exibidos em páginas de artigo único.
- **Visualizações** O número total de vezes que o artigo foi exibido como um artigo único, mostrado na lista de informações do artigo.
- **Links Não Autorizados** Isso afeta os layouts de blog, portanto, o item de menu do blog da categoria relevante deve ter seu valor de *Opções: Links Não Autorizados* definido como *Sim* ou *Usar Configurações do Artigo*. Então, se o *Acesso* deste artigo estiver definido como *Registrado* e a configuração no artigo não for *Não*, o *Texto de Introdução* do artigo será mostrado no layout do blog, mas o rótulo do botão Leia mais será *Registre-se para ler mais...*. Clicar no link Leia mais exigirá login para visualizar o conteúdo completo do artigo.
- **Posição dos links** Refere-se ao posicionamento dos links na aba Imagens e Links, Links A, B e C. A posição padrão é acima do texto do artigo. Esta opção permite que os links sejam colocados abaixo do texto do artigo ou não sejam exibidos.
- **Texto do Leia Mais** O texto normal, *Leia Mais:* seguido do título do artigo é retirado dos valores da chave/string do idioma. Uma substituição personalizada apenas para este artigo pode ser inserida aqui, por exemplo, *Veja o artigo completo:* seguido do título do artigo.
- **Título da Página do Navegador** O título da página geralmente é o título do artigo. Se isso for inconveniente, um título alternativo para a página pode ser inserido aqui para uso na página de artigo único. Ele aparece na aba do navegador e na área `<head>...</head>` da página. Será usado por Motores de Busca.  

*Traduzido por openai.com*
