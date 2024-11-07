<!-- Filename: J4.x:Template_Basics / Display title: Noções Básicas de Modelo  -->

## Introdução

No Joomla!, um template é uma coleção de arquivos que, juntos, definem a aparência do site. O Joomla 4 fornece dois templates: Atum é o template do Administrador usado para a gestão do site; e Cassiopeia é o template do Site usado para os visitantes do site. Muitos outros templates de site estão disponíveis a partir de fornecedores independentes, seja de forma gratuita ou por um preço modesto. De fato, há toda uma indústria baseada na oferta de templates de site especializados.

Um template de site típico contém arquivos PHP para estruturar o conteúdo e arquivos CSS para estilizar o conteúdo. Muitas vezes, existem arquivos adicionais, como imagens usadas no layout e arquivos JavaScript usados para interagir com recursos do site, como links e botões. A captura de tela a seguir mostra as pastas e arquivos do template Cassiopeia em uma nova instalação do Joomla 4:

![captura de tela da página de personalização de templates cassiopeia](../../../en/images/templates/templates-customise-cassiopeia.png)

Note que os arquivos php estão na pasta /templates do site e os arquivos de mídia estão na pasta /media do site.

## Posições do Template

O template do site define as posições do conteúdo principal, como por exemplo um artigo individual ou um layout de blog com artigos em destaque, e quaisquer módulos a serem exibidos acima, abaixo, à esquerda ou à direita do conteúdo principal. A ilustração a seguir mostra as posições disponíveis no Cassiopeia:

![diagrama das posições do template](../../../en/images/templates/cassiopeia-template-positions.png)

Além disso, você pode ver as posições do template em qualquer modelo configurando Pré-visualização das Posições dos Módulos como Habilitado no formulário de Opções do Template e, em seguida, adicionando ?tp=1 à url. Se já houver uma string de consulta anexada à url, então adicione &tp=1 em vez disso.

## Estilo do Usuário

Cassiopeia tem algumas opções que você pode modificar para alterar a aparência do site (existe um artigo separado sobre Personalização do Cassiopeia). Isso pode não ser suficiente para seus propósitos. Você pode fazer suas próprias mudanças na aparência com uma folha de estilo user.css. Você precisa criar isso no formulário Templates:Customizar. Basta selecionar Novo Arquivo e inserir o Nome do Arquivo: user, selecionar Tipo de Arquivo: .css, e escolher css da lista de pastas. Depois selecione o arquivo user.css recém-criado no formulário de Edição e insira alguns estilos, por exemplo, para deixar cabeçalhos verde escuro:
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```

## Sobrescritas de Template

Além do layout geral definido pelo template do site, cada componente ou módulo tem um template para definir sua aparência dentro do layout geral. Esses templates estão localizados em uma pasta tmpl dentro do componente ou módulo. Alguns plugins também possuem templates. E existem layouts que podem ser chamados de qualquer tipo de extensão.

Às vezes, um desses templates de *extensão* não é exatamente do seu agrado. Nesse caso, você pode criar uma sobrescrita de template. Esta é uma cópia do código usado para gerar o layout da extensão para que você possa modificar conforme suas próprias necessidades. A captura de tela a seguir mostra o Template: formulário Personalizar Criar Sobrescritas:

![sobrescritas de template](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Cassiopeia já tem algumas sobrescritas instaladas. Isso pode parecer um problema. Se você alterar qualquer um dos arquivos padrão do Cassiopeia, suas alterações serão sobrescritas (e, portanto, perdidas) na próxima atualização do Joomla. A solução é templates filhos.

## Layouts Alternativos

Um template, ou uma substituição de template, define a aparência de uma extensão em um arquivo específico, como default.php. Em alguns casos, você pode desejar escolher entre o layout padrão e um layout alternativo. Por exemplo, um menu em uma posição superior geralmente precisa de um layout diferente do mesmo menu em uma posição lateral. Em um módulo de menu, há um parâmetro de Layout na aba Avançado do formulário de edição do módulo que permite selecionar entre os layouts alternativos disponíveis. Há um tutorial separado sobre Layouts Alternativos de Template.

## Modelos Filhos

Um modelo filho utiliza os arquivos do modelo pai, exceto por quaisquer arquivos que estejam no modelo filho. Por exemplo, você pode ter diferentes arquivos user.css no pai e no filho para que diferentes páginas possam ter diferentes esquemas de cores. Ou você pode copiar o arquivo index.php do pai para o filho e alterá-lo para produzir um layout diferente do pai. Existe um tutorial separado sobre modelos filhos.

*Traduzido por openai.com*

