<!-- Filename: J4.x:Cassiopeia_Template_Customisation / Display title: Personalização Cassiopeia -->

## Introdução

Cassiopeia é o modelo de site fornecido com o Joomla 4. É um excelente modelo **acessível** e **responsivo** de propósito geral. Ele pode ser personalizado através das opções do template e do arquivo *user.css* por usuários com algum conhecimento de HTML e CSS.

A ilustração a seguir mostra a aparência de um site Joomla 4 com um artigo e alguns itens de menu criados.

![Visualização de artigo único do Cassiopeia](../../../en/images/templates/cassiopeia-customisation-article-view.png)

## Templates: Editar Estilo

Você pode experimentar a aparência do site abrindo o formulário Editar Estilo. Vá para **Sistema → Templates → Estilos de Template do Site** e selecione o título do template na coluna Estilo, Cassiopeia - Padrão. A aba Avançado contém configurações que você pode ajustar:

![Aba avançada de edição de estilo Cassiopeia](../../../en/images/templates/cassiopeia-customisation-edit-style.png)

Para testar as opções, mantenha uma aba ou janela do navegador aberta com a interface Administrativa e uma segunda aba ou janela com a interface do Site, alternando entre as duas após cada alteração salva.

### Marca

- **Sim** o padrão. A barra de logo Cassiopeia contendo um Logotipo ou Nome da Marca é exibida com um fundo escuro, azul por padrão.
- **Não** A barra de logotipo não é exibida. As opções para selecionar um Logotipo, Título e Slogan desaparecem.

A imagem padrão da marca é a palavra Cassiopeia como uma imagem em um arquivo SVG. Isso é o que é exibido na primeira ilustração acima.

Você pode definir Marca como Não se desejar fornecer uma marca em um módulo HTML personalizado.

### Logotipo

- **Nenhum** O logotipo de imagem padrão do Cassiopeia será usado, a menos que um Título seja definido.
- **Imagem do Logotipo** O Logotipo selecionado aparecerá no lugar do logotipo do Cassiopeia, mesmo que um Título esteja definido.

### Título (alternativa ao logotipo)

- **Meu Nome de Marca** Se presente e você não selecionou uma imagem de Logotipo, as palavras no campo Título aparecerão sublinhadas na barra azul superior.

### Slogan

- **Sempre ao seu serviço** Se presente, as palavras no campo de slogan aparecerão em um tamanho de fonte pequeno abaixo da imagem do logotipo ou do Nome da Marca.

![Marca Cassiopeia com slogan](../../../en/images/templates/cassiopeia-customisation-brand-with-tagline.png)

### Esquema de Fontes

- **Nenhum** o padrão. A família de fontes especificada na folha de estilos do template é usada, o que geralmente significa que o site usará as fontes com as quais você está familiarizado, disponíveis em seu próprio computador.
- **Outras** Uma família de fontes localizada na hierarquia da pasta do template ou baixada da web será usada. Você pode ver a aparência alterada do texto em uma página quando recarregar o site após mudar essa opção.

### Tema de Cores

- **Padrão** Uma cor de fundo azul escuro para a barra de Marca e outras funcionalidades, como o botão de Login.
- **Alternativa** Uma cor de fundo marrom escura em vez de azul escuro.

![Esquema de cores alternativo Cassiopeia](../../../en/images/templates/cassiopeia-customisation-alt-color-scheme.png)

### Layout

- **Estático** o padrão. A largura máxima é definida para 1320px. Em telas mais largas, a margem simplesmente se torna maior.
- **Fluído** Não há largura máxima.

A visualização em um dispositivo móvel de tela estreita:

![Visão móvel Cassiopeia](../../../en/images/templates/cassiopeia-customisation-mobile-view.png)

### Cabeçalho Fixo

- **Não** o padrão. Itens e conteúdo do cabeçalho rolam para cima, saindo do campo de visão.
- **Sim** Exceto em telas estreitas, itens do cabeçalho permanecem fixos na parte superior do campo de visão enquanto os itens de conteúdo rolam para cima. Isso é evidente apenas onde o conteúdo da página é mais alto que o campo de visão.

### Link de Voltar ao Topo

- **Não** o padrão. Não há link de Retornar ao topo.
- **Sim** Onde o conteúdo é mais alto que o campo de visão, no canto inferior direito da página, há um botão marcado com um chevron para cima. Selecione-o para rolar de volta ao topo da página.

![Cassiopeia voltar ao topo](../../../en/images/templates/cassiopeia-customisation-back-to-top.png)

## Posições do Modelo Cassiopeia

Ao construir um site com o Cassiopeia, é realmente útil saber as localizações das posições que você pode usar para módulos. Algumas são descritivas, como *menu* e *bottom-a*, mas não é tão óbvio onde elas estão até que você as utilize. Esta ilustração deve ajudar:

![Posições do modelo Cassiopeia](../../../en/images/templates/cassiopeia-template-positions.png)

Experimente o seguinte:

### Mover o Módulo de Menu para a Posição *menu*

Um site recém-instalado do Joomla 4 tem um menu na posição *sidebar-right*, conforme visto na primeira ilustração acima. Para este tutorial, alguns itens de menu foram adicionados, sendo um deles um pai com dois itens filhos. Para mover este menu para a posição de menu, vá para **Conteúdo** → **Módulos do Site** no menu do Administrador. Na lista, há três módulos, incluindo o Menu Principal. Selecione-o para abrir o formulário de edição de Módulos: Menu.

Na aba Módulo, altere o campo de Posição à direita para Menu \[menu\]. Salve e veja o resultado na exibição do site. O menu parece bom, mas os itens filhos não estão lá.

No formulário de edição do menu, selecione a aba Avançado e role para baixo até o campo Layout. É uma lista suspensa com quatro opções. --Do Módulo-- / Padrão é selecionado por padrão. Experimente as outras opções e veja o resultado. (Lembre-se de *Salvar* no formulário de edição e recarregar na exibição do site.) Nenhuma das opções --Do Módulo-- mostra os itens do menu filho, mas ambas as opções --Do Modelo Cassiopeia-- sim.

![Posições do menu Cassiopeia](../../../en/images/templates/cassiopeia-customisation-menu-position.png)

Então, qual é a diferença que o **Recolhível** faz?

- Dropdown Recolhível: Em dispositivos móveis com tela estreita, o menu se recolhe para um ícone de Hambúrguer até ser selecionado. Ao ser selecionado, ele se expande para mostrar uma lista vertical.
- Dropdown: O menu sempre aparece como uma lista vertical.

### Mover o Módulo de Menu para a Posição *topbar*

No formulário de edição na aba Módulo, defina a Posição para Barra Superior \[topbar\] e veja o resultado. Há um problema - o menu está posicionado mais à esquerda do que quando estava na posição de menu. Isso ocorre porque a posição do menu e a localização do logotipo têm uma classe CSS de *grid-child*, mas a barra superior não tem. Isso pode ser corrigido com uma entrada no arquivo *user.css*, a seguir.

## Personalizar Cassiopeia

E se você não gostar da cor de fundo azul escuro do cabeçalho? 
Suponha que você prefira um tema verde escuro. Para corrigir isso, você precisa de um pouco de conhecimento em CSS. Vá para **Sistema** → **Modelos de Site** → **Detalhes e Arquivos do Cassiopeia** para abrir o formulário de Personalização do Modelo (Cassiopeia).

A ilustração abaixo mostra dois grupos de pastas. O primeiro grupo consiste nas pastas e arquivos do modelo que você não deve alterar, mas aos quais você pode adicionar. Em particular, você pode adicionar arquivos HTML de substituição de modelo à pasta *html*. O segundo grupo contém os arquivos de mídia do modelo que você não deve alterar. Porém, você pode adicionar um arquivo *user.css* à pasta *css* e/ou um arquivo *user.js* à pasta *js*. Você faria isso se quisesse fazer algumas alterações simples na aparência do site.

![Cassiopeia editar arquivos](../../../en/images/templates/cassiopeia-customisation-edit-files.png)

Note que não há um arquivo *user.css* presente na pasta *css*. Esse é um arquivo que você cria para poder substituir estilos previamente definidos. Se não estiver presente, crie-o agora selecionando a pasta *css* e depois o botão *Novo*. No diálogo modal Novo Arquivo, selecione a pasta *css*, caso contrário, o novo arquivo aparecerá no local errado. Digite user (em minúsculas e sem *.css*) no campo Nome do Arquivo e selecione *.css* no campo Tipo de Arquivo. Selecione o botão Criar para criar o arquivo. Se *user.css* já estiver presente, selecione-o para abrir o formulário de edição.

### Cabeçalhos

Como um início simples, altere a cor dos cabeçalhos para verde escuro. Cabeçalhos são tags na faixa *h1, h2, h3, h4, h5* e *h6*. No arquivo *user.css*, insira a definição de estilo:
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```
Salve e recarregue o site para ver o resultado. O título da Página ou do Artigo deve ser verde escuro. Se não for, verifique o que você digitou. O idioma formal para a documentação do Joomla é o inglês britânico, então é colour ao invés de color como no inglês americano. Mas em CSS deve ser color. A pontuação está correta?

Não é tão óbvio que algumas tags além dos cabeçalhos podem ser estilizadas para parecer cabeçalhos. Então, adicione isto:
```css
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
```
Note aqui que o ponto (.) inicial é um seletor de classe, por exemplo, Dummy H1 - então há um ponto no arquivo CSS, mas não no nome da classe.

### Fundo do Cabeçalho

Na aba do navegador contendo o Site, abra as Ferramentas do Desenvolvedor do navegador, neste exemplo Firefox, e selecione a tag do cabeçalho.

![Ferramentas de desenvolvedor Cassiopeia](../../../en/images/templates/cassiopeia-customisation-developer-tools.png)

Isso mostra os estilos usados. O estilo container-header é onde a cor de fundo e a imagem de fundo são definidas. Eles precisam ser substituídos no arquivo *user.css*. Tente isto:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
```
### Estilo *topbar*

Lembre-se daquele comentário sobre o menu estar muito à esquerda na barra superior? Isso ocorre porque ele não tem uma largura máxima e margens apropriadas definidas. Coloque isto no arquivo *user.css* para corrigir isso:
```css
    .container-topbar {
      max-width: 1320px;
      margin-left: auto;
      margin-right: auto;
    }
```
Este é o tema verde funcionando:

![Tema verde Cassiopeia](../../../en/images/templates/cassiopeia-customisation-green-theme.png)

### Acessibilidade

Note que deve haver um contraste suficiente entre as cores de fundo e de primeiro plano para atender aos padrões de acessibilidade web. Você pode verificar seu contraste no Verificador de Contraste do WebAIM. Verde escuro é \#006400.

## Substituições

A aba Criar Substituições do formulário Templates: Personalizar (Cassiopeia) mostra a lista de extensões para as quais você pode criar uma substituição. Note os diferentes símbolos: selecione um símbolo de pasta para mostrar uma lista das pastas e arquivos que ela contém; selecione um símbolo de múltiplos arquivos para criar imediatamente uma substituição para essa extensão; o item criado desaparece da lista - selecione a aba Editor e localize a substituição criada na pasta *html*. Pode haver mais de um arquivo criado - os arquivos criados são copiados da extensão original prontos para você editar. Para isso, você precisa ter algum conhecimento de HTML e PHP!

Esta é a aba Criar Substituições:

![Cassiopeia criar substituições](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Se você está apenas experimentando e realmente não deseja uma substituição, pode *Fechar* o formulário de edição, selecionar o botão Gerenciar Pastas na barra de ferramentas e selecionar o botão Excluir na parte inferior do formulário modal Gerenciar Pastas.

As substituições são realmente sobre personalizar extensões em vez do template Cassiopeia e essa é outra história.

## Templates Filhos

Se você deseja fazer alterações mais substanciais na aparência do site, pode criar um template filho. Isso copia apenas uma pequena seleção de pastas e arquivos para você alterar ou adicionar, mas continua a usar as pastas e arquivos do template pai. Ao usar templates filhos, você pode ter algumas páginas com uma cor de tema e outras páginas com uma segunda cor de tema. Templates filhos são abordados em outro lugar. Esta é uma ilustração da estrutura de arquivos em um filho de Cassiopeia:

![Arquivos do template filho de Cassiopeia](../../../en/images/templates/cassiopeia-customisation-child-template-files.png)

*Traduzido por openai.com*

