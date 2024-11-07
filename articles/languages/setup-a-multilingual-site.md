<!-- Filename: J4.x:Setup_a_Multilingual_Site / Display title: Configurar um Site Multilíngue  -->

## Dados de Exemplo

O Joomla vem com dois conjuntos de dados de exemplo: Blog e Multilíngue. Há um terceiro conjunto de Teste, mas apenas para usuários que trabalham com a versão de Desenvolvimento do Joomla. Se você tem um site existente com artigos, menus e módulos, ele será semelhante, em princípio, a um site com dados de exemplo do Blog instalados.

No Painel Inicial, os dados de exemplo Multilíngue dizem **Antes de iniciar, certifique-se de ter pelo menos 2 idiomas instalados com seus Idiomas de Conteúdo e que nenhum dado de exemplo foi instalado**. Isso provavelmente levará você a criar um site multilíngue executando manualmente as etapas necessárias uma a uma. Esse é um procedimento propenso a erros em que você pode cometer um erro, especialmente se estiver usando vários idiomas. Os erros podem ser corrigidos, mas todo o processo é um pouco tedioso e pode ser confuso.

Você pode ignorar esse conselho e usar os Dados de Exemplo Multilíngue para configurar um site multilíngue se entender como fazer algumas correções nos menus e módulos originais mais tarde.  

## Site Inicial

Um site Joomla recém-instalado possui um **Menu Principal** na barra lateral direita. Ele contém um único item de menu chamado **Início** do tipo Artigos em Destaque. Há também um **Formulário de Login** na barra lateral direita.

Inicialmente, não há artigos em destaque, então a parte principal da página está vazia.

## Exemplo de Dados para Blog

Se você criou o conteúdo do seu próprio site, **não** deve instalar o Exemplo de Dados para Blog. No entanto, leia esta seção para ver como ele se compara. Caso contrário:

- Selecione **Instalar** na seção de Exemplo de Dados Multilíngue do Dashboard Principal. As etapas de instalação aparecerão brevemente e, em seguida, desaparecerão.
- Você deverá notar que vários novos menus são instalados (recarregue a página do administrador e expanda o menu Menus):
  - Menu Principal Blog.
  - Menu Inferior, contendo os itens de menu Login/Sair.
  - Menu Especial, visto após o login.
- Selecione o ícone **Abrir frontend** na barra de status superior ou recarregue o site se ele já estiver aberto em uma guia separada.

Você deverá esperar ver um layout cheio de informações de Artigos em Destaque:

- No topo está o novo menu **Menu Principal Blog** para vários layouts e artigos de blog.
- Na barra lateral direita, há módulos para um Formulário de Login, um Menu Principal e um feed RSS do Meu Blog.
- Após o login, a barra lateral direita tem um Menu Especial para ações exclusivas do Administrador.
- O item **Home** do Menu Principal leva ao layout de Artigos em Destaque.
- O item de menu superior **Blog** leva a um layout de Categoria de Blog um pouco diferente do layout de Artigos em Destaque.

Dedique alguns minutos para explorar os itens de menu e os tipos de informação a que eles levam.

## Instalar e Publicar Idiomas de Conteúdo

Primeiro, instale todos os idiomas que você pretende usar. Se precisar instalar um idioma adicional mais tarde, você precisará completar as etapas de configuração para esse idioma manualmente, uma por uma. Isso será abordado em outra parte. Para este tutorial, o francês, o alemão e o galês foram adicionados ao idioma padrão em inglês do site durante a instalação do Joomla. Para adicionar idiomas após a instalação:

- Selecione **Sistema**→**Instalar Idiomas** no menu do Administrador.
- Selecione o botão **Instalar** para cada idioma que você pretende usar.

Os idiomas instalados devem ser **Publicados** para ficarem disponíveis. No menu do Administrador:

* Selecione **Sistema / Painel de Gerenciamento / Idiomas de Conteúdo**
* Na coluna de Status, **Publique** cada um dos idiomas que você deseja usar.

## Dados de Amostra Multilíngue

A instalação dos Dados de Amostra Multilíngue tem efeitos que você terá que lidar posteriormente:

- Menus na barra lateral direita serão despublicados. Isso significa que o módulo do Menu Principal será despublicado e não haverá link para o layout de Artigos em Destaque. Se você tinha outros links no Menu Principal, eles também ficarão indisponíveis.
- O Menu Especial será despublicado. Isso fornecia um link para criar uma nova postagem.

Os Dados de Amostra Multilíngue oferecem os seguintes recursos adicionais:

- Uma categoria de artigo para cada idioma.
- Um artigo configurado para cada idioma, embora em texto pseudo Lorem ipsum.
- Um menu separado para cada idioma. Você verá isso na lista **Administrador**→**Menus**.
- Um módulo de menu **Menu Principal xx-YY** na barra lateral direita do Site, onde xx-YY é um código de idioma como en-GB.
- O item de menu **Principal** agora leva a um layout de Blog de Categoria para artigos no Idioma selecionado. Ele contém apenas um artigo.
- Há um módulo **Seletor de Idiomas** na barra lateral direita. Ele está sem título para evitar a necessidade de um módulo separado para cada idioma com títulos traduzidos. A seleção é feita pela bandeira do idioma. Experimente.

Algo a notar: palavras fornecidas pelo Joomla serão traduzidas, por exemplo no Breadcrumbs e no Formulário de Login. Palavras digitadas pelos usuários precisam ser traduzidas manualmente, por exemplo Formulário de Login e Menu Principal. Mais sobre isso mais tarde.

## Corrigindo Problemas Iniciais

### Ordem dos Idiomas

Você pode notar que o alternador de idioma exibe os idiomas em ordem alfabética inversa. Para alterar a ordem:

- Selecione **Sistema → Idiomas de Conteúdo** no menu do Administrador.
- Use os ícones de elipse vertical para arrastar os idiomas na ordem desejada.
- Recarregue o Site e veja que o Alternador de Idioma agora tem os idiomas na sua ordem preferida.

### Ordem dos Módulos da Barra Lateral Direita

A ordem dos módulos na barra lateral direita é uma questão de preferência pessoal. Para alterar a ordem:

- Selecione **Conteúdo → Módulos do Site** no menu do Administrador.
- Filtre por **Posição → barra-lateral-direita**.
- Selecione o ícone da coluna de ordem para revelar as alças de arrasto de ordenação (ícones de elipse vertical). O ícone do cabeçalho da coluna deve ser um chevron apontando para cima.
- Arraste os itens para a ordem desejada:
  - Alternador de Idioma
  - Menu Principal (todas as variantes - a ordem não importa).
  - Menu Especial
  - Formulário de Login
  - Artigos Arquivados
  - Sindicação

### Artigos em Destaque

O Menu Principal original não está publicado, mas o item de menu Home que ele contém pode ser reproduzido em outro lugar. O lugar mais conveniente é o menu superior.

- Selecione **Menus → Menu Principal Blog** no menu do Administrador.
- Selecione o botão **Novo** na Barra de Ferramentas.
- Insira um **Título** no formulário **Menus: Novo Item**, por exemplo, **Destaque**.
- Use o botão **Selecionar** no campo **Tipo de Item de Menu**.
- Selecione **Artigos → Artigos em Destaque** na lista de **Tipo de Item de Menu**.
- Selecione **Salvar** na Barra de Ferramentas.
- No campo **Ordenação**, selecione **- Primeiro -**.
- Na guia **Layout do Blog**, defina **Artigos de Introdução** para 3.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.

### Atribuição de Módulo do Site

O layout original dos Artigos em Destaque da página inicial foi produzido atribuindo módulos selecionados para aparecerem apenas naquela página. A nova página de Destaque precisa ser adicionada para cada um desses módulos.

- Selecione **conteúdo → Módulos do Site** no menu do Administrador.
- Encontre e selecione o item **Imagem**.
- Na guia **Atribuição de Menu**, encontre e marque o item **Destaque** na seção **Menu Principal Blog**.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.
- Encontre e selecione o item **Últimas Postagens**.
- Na guia **Atribuição de Menu**, encontre e marque o item **Destaque** na seção **Menu Principal Blog**.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.

## Recarregar Site

Quando você recarregar o site, o primeiro item no menu superior será o link em Destaque que leva ao layout de Artigos em Destaque. O item Blog adjacente é um layout de Blog de Categoria mais compacto. Experimente o alternador de idiomas. O texto fornecido pelo Joomla, nos links de navegação e no Formulário de Login, muda de acordo. Além disso, os artigos em Destaque agora incluem um artigo dos Dados de Amostra Multilíngues, que está no idioma selecionado. Pode estar na última página.

### Site Multilíngue Híbrido ou Puro

Neste estágio, você tem um site híbrido: algum conteúdo está disponível em todos os idiomas e outro conteúdo está disponível em um idioma específico. Se você quiser um site puramente Multilíngue, precisará despublicar o módulo Blog do Menu Principal superior e, talvez, outros. Em alguns casos, você pode desejar criar módulos específicos para cada idioma, por exemplo, o Formulário de Login poderia ter versões com os títulos Formulaire de connexion, Login Formular e Ffurflen Mewngofnodi.

O que você faz a seguir depende de você!

## Menu Principal Original

Seu módulo de Menu Principal original, que agora não está publicado, pode ter
contido itens de menu adicionais. Você poderia publicá-lo. O problema é que o
item Início está vinculado ao mesmo local que cada uma das páginas iniciais dos
menus específicos de idioma, mas apenas em inglês. Você pode resolver isso da
seguinte forma:

- Selecione **Menus**→**Menu Principal** no menu do Administrador.
- Selecione o item de menu **Início**.
- Selecione a aba **Tipo de Link**.
- Defina **Exibir no Menu** como **Não**.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.
- Selecione **Conteúdo**→**Módulos do Site** no menu do Administrador.
- Encontre o **Menu Principal** e publique-o, transformando o X cinza em um
  tick verde.

Os itens visíveis no Menu Principal original agora devem funcionar normalmente. Se o
Menu Principal não tiver itens visíveis, ele não será exibido.

## Adicionando um Idioma Extra

Após a configuração inicial de um site multilíngue, se você deseja adicionar outro idioma, terá que seguir as etapas manualmente, uma por uma:

### Passo 1: Instalar o Idioma

- Selecione **Sistema**→**Instalar**→**Idiomas** no menu do Administrador.
- Encontre o idioma necessário na lista de **Extensões: Idiomas**.
- Selecione o botão **Instalar**.
- Haverá uma mensagem: **Instalação do pacote de idioma bem-sucedida.**

Neste exemplo, o idioma extra é o Espanhol.

### Passo 2: Publicar e Ordenar

- Selecione **Sistema**→**Gerenciar**→**Idiomas de Conteúdo** no menu do Administrador.
- Habilite o idioma recém-instalado: selecione o botão de Status para transformar o cruzamento cinza em um tique verde.
- Use os ícones de elipse vertical para arrastar os idiomas na ordem desejada.

### Passo 3: Criar um Menu

- Selecione **Menus**→**Gerenciar** no menu do Administrador.
- Selecione o botão **Novo** na Barra de Ferramentas.
- Insira um título de menu adequado e um nome único, exemplos: Menu Principal (es-ES) e menuprincipal-es-es.
- Insira uma Descrição, exemplo: O menu principal do site no idioma Espanhol (es-ES).

### Passo 4: Adicionar um Módulo de Menu

- Selecione **Menus**→**Gerenciar** no menu do Administrador.
- Selecione o botão **Adicionar um módulo para este menu** para o menu recém-criado.
- Insira um título adequado, exemplo: Menu Principal es-ES
- Selecione uma Posição: Sidebar-direita
- Selecione um Idioma: Espanhol (es-ES)
- Selecione **Salvar**.
- Ordene o módulo: na lista Ordenar, selecione o item após o qual este novo item deve aparecer.
- Selecione **Salvar & Fechar**.

### Passo 5: Adicionar uma Categoria

- Selecione **Conteúdo**→**Categorias** no menu do Administrador.
- Selecione o botão **Novo** na Barra de Ferramentas.
- Insira um título adequado, exemplo: Categoría (es-es)
- Selecione o idioma correto: Espanhol (es-ES)
- Selecione a aba **Associações**.
- Para cada idioma, selecione uma Categoria. Há apenas uma escolha em cada caso.
- Selecione **Salvar & Fechar**.

### Passo 6: Adicionar um Item de Menu

- Selecione **Menus**→**Menu Principal (es-ES)**, o menu recém-criado.
- Selecione o botão **Novo** na Barra de Ferramentas.
- Insira um título adequado, exemplo: Página de Início
- Use o botão Selecionar no final do campo **Tipo de Item de Menu** para selecionar um tipo de item.
- Na lista pop-up, selecione **Artigos**→**Blog de Categoria**.
- No campo Escolher uma Categoria, use o botão Selecionar.
- Na lista pop-up de Categorias, selecione a categoria Categoría (es-es).
- Defina o campo **Página Padrão** como **Sim**.
- Na lista suspensa **Idioma** selecione **Espanhol (es-ES)**.
- **Salvar & Fechar**

### Passo 7: Adicionar um Artigo

A maneira fácil de adicionar um artigo para o novo idioma é copiar um artigo existente.

- Selecione **Conteúdo**→**Artigos** no menu do Administrador.
- Selecione o artigo para copiar, neste exemplo **Artigo (en-GB)**.
- No formulário **Artigos: Editar**, altere o título para **Artigo (es-ES)**.
- Altere a **Categoria** para **Categoria (es-es) (es-ES)**.
- Altere o **Idioma** para Espanhol (es-ES)**.**
- Selecione **Salvar como Cópia** na lista suspensa **Salvar & Fechar** na Barra de Ferramentas. **Cuidado!**
- Selecione a aba **Associações**.
- Para cada idioma, selecione um artigo a ser associado - o artigo equivalente em cada idioma.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.

## Adicionando um Artigo Multilíngue

Suponha que você deseje criar um artigo em cada um dos idiomas selecionados.

- Selecione **Conteúdo** → **Artigos** → **+** no menu do Administrador
  ou o botão **Novo** na Barra de Ferramentas na lista de Artigos.
- Insira um título para o artigo, exemplo **William Shakespeare**.
- Defina o campo **Categoria** para **Category (en-gb) (en-GB)**.
- Defina o campo **Idioma** para **Inglês (en-GB)**.
- Insira o **Texto do Artigo**, exemplo da Wikipedia:

“William Shakespeare (batizado em 26 de abril de 1564 – 23 de abril de 1616) foi um
dramaturgo, poeta e ator inglês. Ele é amplamente considerado o maior escritor da língua inglesa e o maior
dramaturgo do mundo. Ele é frequentemente chamado de poeta nacional da Inglaterra e de "Bardo de
Avon" (ou simplesmente "o Bardo"). Suas obras existentes, incluindo
colaborações, consistem em cerca de 39 peças, 154 sonetos, três longos
poemas narrativos e alguns outros versos, alguns de autoria incerta.
Suas peças foram traduzidas para todos os principais idiomas vivos e são
representadas mais frequentemente do que as de qualquer outro dramaturgo. Ele continua a ser
provavelmente o escritor mais influente na língua inglesa, e suas
obras continuam a ser estudadas e reinterpretadas.”

- Selecione **Salvar** na Barra de Ferramentas.
- Selecione a aba **Associações**.
- Para cada idioma:
  - Selecione o botão **Criar**.
  - No formulário popup **Novo Artigo** insira um título traduzido,
    **William Shakespeare**.
  - Defina a Categoria para a do idioma que você selecionou.
  - Insira o texto traduzido no campo **Texto do Artigo** (você pode
    tentar <a href="https://translate.google.com/"
    rel="nofollow noreferrer noopener">https://translate.google.com/</a>).
  - Selecione **Salvar e Fechar**.
- Depois que um novo artigo para cada idioma tiver sido criado, selecione **Salvar
  e Fechar**.

## Menu Principal

Se você tem um link para um artigo para Todos os Idiomas no Menu Principal e, posteriormente, usa esse artigo como base para artigos associados em outros idiomas, você precisará alterar o link do Menu Principal. Caso contrário, alternar idiomas com esse artigo selecionado resultará em um erro de Página Não Encontrada no idioma selecionado.

- Selecione **Menus** → **Menu Principal** no menu do Administrador.
- Selecione o item de menu que você precisa alterar, por exemplo, **William Shakespeare**.
- Altere o campo **Idioma** para **Inglês (en-GB)**.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.

Se houver apenas esse item no Menu Principal, aquele módulo desaparecerá ao alternar para outros idiomas.

*Traduzido por openai.com*

