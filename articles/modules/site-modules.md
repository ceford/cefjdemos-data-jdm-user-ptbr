<!-- Filename: J4.x:Site_Modules / Display title: Módulos do Site -->

## Introdução

Módulos são extensões leves e flexíveis usadas para renderizar trechos de informação em **caixas** dispostas ao redor de um componente em uma página. Um exemplo bem conhecido é o módulo de login. Os módulos são atribuídos por item de menu, então você pode decidir mostrar ou esconder um módulo dependendo de qual página o usuário está visualizando no momento.

Alguns módulos estão ligados a componentes. Por exemplo, o módulo **Notícias Mais Recentes** está conectado ao componente de conteúdo para exibir links para os artigos mais novos. Módulos não precisam estar vinculados a componentes. Eles nem sequer precisam estar ligados a nada e podem ser simplesmente HTML ou texto estático.

Pode haver múltiplas instâncias do mesmo módulo. Por exemplo, você pode usar uma instância do módulo de Imagem Aleatória para algumas páginas e outra instância para outras páginas, cada uma utilizando uma pasta de imagens diferente para selecionar as imagens.

## Posições de Módulos

Os módulos são atribuídos a uma posição em uma página definida pelo template em uso. A ilustração a seguir mostra um layout esquemático do template Cassiopeia:

![Diagrama de posições do template Cassiopeia](../../../en/images/modules/cassiopeia-template-positions.png)

E a lista a seguir mostra as posições de módulos disponíveis por nome:

```xml
    <positions>
        <position>topbar</position>
        <position>abaixo-topo</position>
        <position>menu</position>
        <position>busca</position>
        <position>banner</position>
        <position>topo-a</position>
        <position>topo-b</position>
        <position>principal-topo</position>
        <position>principal-rodapé</position>
        <position>caminho</position>
        <position>barra-lateral-esquerda</position>
        <position>barra-lateral-direita</position>
        <position>inferior-a</position>
        <position>inferior-b</position>
        <position>rodapé</position>
        <position>depuração</position>
    </positions>
```

## Adicionar um Módulo Core

Os módulos core são aqueles fornecidos com uma nova instalação do Joomla. Existem milhares de módulos adicionais disponíveis de fornecedores terceiros. Suponha que você gostaria de mostrar uma imagem aleatória para tornar seu site mais interessante para os visitantes. No menu do Administrador, selecione **Conteúdo → Módulos do Site** para ver a lista de módulos do site já em uso:

![Lista de Módulos do Site](../../../en/images/modules/cassiopeia-modules-list.png)

Selecione o botão Novo para ver uma lista de módulos do site disponíveis para instalação:

![Módulos do Site disponíveis](../../../en/images/modules/cassiopeia-modules-available.png)

Desça e selecione o módulo Imagem Aleatória. Isso abrirá o formulário de edição **Módulos: Imagem Aleatória** pronto para você preencher.

![Módulo de imagem aleatória](../../../en/images/modules/cassiopeia-module-random-image.png)

- **Título** Este campo é obrigatório.
- **Tipo de Imagem** O padrão é jpg.
- **Pasta de Imagem** Insira um caminho para uma pasta que realmente contenha
  imagens do tipo que você selecionou.
- **Link** Um URL para redirecionar se a imagem for selecionada.
- **Largura** Força todas as imagens a serem exibidas com essa largura em pixels.
- **Altura** Deixe vazio para manter a proporção da imagem.
- **Posição** Selecione uma posição do módulo para que o módulo realmente
  apareça em uma página. Na ilustração, foi selecionado lado-direito.
- **Salvar & Fechar** Ou use o botão de Ajuda na Barra de Ferramentas para
  descobrir o que os outros campos fazem.

## Ordem dos Módulos

Após salvar, talvez seja necessário alterar a ordem dos módulos na posição escolhida. Proceda da seguinte forma:

- Na lista de Módulos, selecione o ícone de Ordenação de Colunas no cabeçalho da tabela de módulos; é um triângulo combinado para cima/baixo. Isso ordenará a tabela e exibirá símbolos de alça para os itens, uma elipse vertical. Selecione novamente para inverter a ordem de classificação! O símbolo de ordenação da coluna muda: triângulo para cima para indicar ordem de classificação normal, triângulo para baixo para indicar ordem de classificação inversa.
- Pegue e arraste a elipse da Imagem Aleatória para movê-la para cima ou para baixo. Solte quando estiver na posição desejada.

## Visualizar o Site

![Visualização do módulo de imagem aleatória no site](../../../en/images/modules/cassiopeia-module-random-image-site.png)

Verifique a aparência do Site. Neste caso, pode ser uma boa ideia centralizar a imagem. Isso pode ser feito da seguinte maneira:

- Volte para o formulário de edição e selecione a Aba Avançado.
- No campo Classe do Módulo, insira text-center e Salve.
- Veja o resultado recarregando a página do Site.

Tudo pronto?

## Lista de Módulos Principais

- **Artigos - Arquivados** Este módulo mostra uma lista dos meses do calendário contendo Artigos Arquivados. Após você alterar o status de um Artigo para Arquivado, esta lista será gerada automaticamente.
- **Artigos - Categorias** Este módulo exibe uma lista de categorias de uma categoria pai.
- **Artigos - Categoria** Este módulo exibe uma lista de artigos de uma ou mais categorias.
- **Artigos - Mais Recentes** Este módulo mostra uma lista dos Artigos mais recentemente publicados e atuais.
- **Artigos - Mais Lidos** Este módulo mostra uma lista dos Artigos publicados que têm o maior número de visualizações de página.
- **Artigos - Newsflash** O Módulo Newsflash exibirá um número fixo de artigos de uma categoria específica.
- **Artigos - Relacionados** Este módulo exibe outros Artigos que estão relacionados ao que está sendo visualizado. Essas relações são estabelecidas pelas Palavras-chave. Todas as palavras-chave do Artigo atual são pesquisadas contra todas as...
- **Banners** O Módulo Banner exibe os Banners ativos do Componente.
- **Breadcrumbs (Navegação Hierárquica)** Este módulo exibe a Navegação Hierárquica.
- **Personalizado** Este módulo permite que você crie seu próprio Módulo usando um editor WYSIWYG.
- **Exibição de Feed** Este módulo permite a exibição de um feed sindicado.
- **Rodapé** Este módulo mostra as informações de direitos autorais do Joomla!.
- **Alternador de Idiomas** Este módulo exibe um alternador de idiomas no seu site dos idiomas de conteúdo disponíveis.
- **Usuários Recentes** Este módulo exibe os usuários mais recentemente registrados.
- **Login** Este módulo exibe um formulário de login com nome de usuário e senha. Ele também exibe um link para recuperar uma senha esquecida. Se o registro de usuário estiver habilitado (em Usuários → Gerenciar → Opções),...
- **Menu** Este módulo exibe um menu no Frontend.
- **Imagem Aleatória** Este módulo exibe uma imagem aleatória da sua pasta escolhida.
- **Busca Inteligente** Este é um módulo de busca para o sistema de Busca Inteligente.
- **Estatísticas** O Módulo de Estatísticas mostra informações sobre a instalação do seu servidor juntamente com estatísticas sobre os usuários do site e o número de Artigos no seu banco de dados.
- **Feeds de Sindicação** Módulo de Sindicação Inteligente que cria um Feed Sindicado para a página onde o Módulo está exibido.
- **Tags - Populares** Este módulo exibe tags usadas no site em uma lista ou layout de nuvem. As tags podem ser ordenadas por título ou pelo número de itens marcados e limitadas a um período de tempo específico.
- **Tags - Similares** O Módulo de Tags Similares exibe links para outros itens com tags similares. A proximidade da correspondência pode ser especificada.
- **Quem Está Online** O Módulo Quem Está Online exibe o número de Usuários Anônimos (Visitantes) e Usuários Registrados (usuários logados) que estão atualmente acessando o site.
- **Wrapper (Envoltório)** Este módulo mostra uma janela iframe para a localização especificada.

*Traduzido por openai.com*
