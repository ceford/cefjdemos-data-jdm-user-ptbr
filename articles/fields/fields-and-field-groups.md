<!-- Filename: J4.x:Fields_and_Field_Groups / Display title: Campos e Grupos de Campos  -->

## Introdução

Campos são usados para exibir atributos adicionais de Artigos, Contatos ou Usuários. Os dados são inseridos em um formulário de Edição do Administrador e exibidos no Site. Um exemplo:

Suponha que você escreva artigos sobre aspectos da natureza, às vezes sobre Flores, outras vezes sobre Animais. Um campo que você talvez queira registrar e exibir para ambos é o Nome Latim, exigindo um campo de texto. Outro pode ser o Habitat: Floresta, Lagoa, Pradaria, e assim por diante, exigindo uma lista suspensa. Para flores, você pode querer registrar a Estação de Florescimento usando 4 caixas de seleção, uma para cada estação, ou 12 caixas de seleção, uma para cada mês.

Campos vazios no formulário de entrada não são exibidos na saída do Site, então você poderia manter todos os campos em uma lista longa. No entanto, geralmente é melhor usar categorias para seus Artigos, digamos Flores e Animais. Campos podem ser atribuídos a mais de uma Categoria. Assim, os campos Nome Latim e Habitat seriam atribuídos a ambos, mas Estação de Florescimento seria atribuído apenas à categoria Flores.

Se um campo não for atribuído a um grupo, ele aparecerá no formulário de Edição em uma aba de Campos. Se um campo for atribuído a um grupo, ele aparecerá em uma aba com esse nome. Portanto, para o grupo de Flores, parece apropriado criar um grupo de campos chamado Dados de Flores (ou apenas Flores, embora usar o mesmo nome para coisas diferentes possa ser confuso). E para os outros campos comuns, você poderia usar um grupo chamado Natureza.

## Um Exemplo Prático - Anotações sobre a Natureza

Para artigos sobre a Natureza, a categoria do artigo e as subcategorias para cada ramo do mundo vivo podem aparecer como no exemplo a seguir:

![Categorias de artigos sobre a natureza](../../../en/images/fields/fields-articles-categories-list.png)

Algumas características óbvias da Natureza a serem observadas:

- A categoria Natureza é para artigos que são sobre a natureza em geral, em vez de tipos específicos de plantas ou animais.
- As subcategorias são para artigos que são mais específicos e podem precisar de suas próprias subcategorias.
- Todas as formas de vida possuem Nomes Comuns e Nomes Latinos.
- Flores e Árvores têm Estação de Florescimento, Altura e Espalhamento, mas Pássaros e Mamíferos não.
- Pássaros têm Envergadura e Comprimento, enquanto Mamíferos têm Altura e Comprimento.
- A Cor pode ser constante ou variada.

O ponto aqui é que pode ser necessário configurar Campos ou Grupos de Campos para características comuns, como Nome Latino, e Grupos de Campos separados para cada categoria de natureza.

## Grupos de Campos

Criar Grupos de Campos para Artigos é muito simples:

- Selecione **Conteúdo → Grupos de Campos** no menu do Administrador
- Selecione o botão **Novo** na barra de ferramentas.
- Insira um **Título** adequado.
- Insira uma **Descrição**. Esta aparece abaixo do campo no formulário de edição do artigo quando *Alternar Ajuda Inline* é selecionado.
- Selecione **Salvar & Fechar** na barra de ferramentas.

![Lista de grupos de campos de conteúdo](../../../en/images/fields/fields-field-groups-list.png)

### Ordenação

Na inserção de dados do artigo, os grupos de campos aparecerão na ordem vista nesta lista. Arraste e solte os itens para mudar a ordem.

## Campos

Para criar um novo Campo de Artigo, selecione **Conteúdo → Campos** no
menu do Administrador e preencha o formulário. Alguns exemplos estão ilustrados
abaixo.

### Texto - Nome Latim

Note que na captura de tela abaixo este campo foi atribuído ao grupo de campos Natureza
e à categoria Natureza. Isso garante que ele sempre apareça em 
artigos na categoria Natureza e em qualquer subcategoria.

![Campo de texto - nome latim no grupo natureza](../../../en/images/fields/fields-latin-name.png)

### Caixas de seleção - Estação de Floração

Caixas de seleção aparecem no formulário de Edição de Artigo para você marcar a selecionar a
estação de floração. Na exibição do artigo, somente aqueles marcados serão
listados. Por exemplo, se você marcar Primavera e Verão, a saída mostrará
Estação de Floração: Primavera, Verão.

Note que nesta captura de tela o Campo foi atribuído ao grupo Flores
e à Categoria Flores. Isso deve garantir que o campo esteja presente apenas em artigos sobre flores.

![Campo de caixa de seleção - estação de floração](../../../en/images/fields/fields-flowering-season.png)

### Cor - Cor

Só para confundir, o nome do tipo de campo é Color (Ortografia dos EUA)
mas o rótulo na documentação é Colour (Ortografia Britânica).

![Campo de cor](../../../en/images/fields/fields-colour.png)

O campo Cor é atribuído ao grupo de campos Natureza e à categoria Natureza
pois não é exclusivo para flores.

### Inteiro - Resistência

A resistência de uma planta pode ser representada como um número inteiro de 1 a 7. Não 
há campo para número real, então comprimento e largura podem ser inteiros com uma escala 
(cm ou m ou ft) incluída no rótulo. Há configurações de *Prefixo* e *Sufixo*
na aba *Opções*. Se não houver um limite superior óbvio, deixe o campo *Último:*
vazio.

![Campo de resistência](../../../en/images/fields/fields-hardiness.png)

RHS Resistência é uma propriedade geralmente aplicada a flores!

Há um problema com o campo inteiro. Ele sempre tem um valor e assim sempre
aparece na saída. Você pode resolver esse problema com uma substituição de template
para *Plugins / Inteiro*. Por exemplo, você poderia usar um valor acima ou abaixo dos
limites esperados para omitir o campo da saída.

## Formulário de Edição de Artigo

Quando um formulário de Artigos: Novo é aberto, a Categoria padrão é
Não Categorizado e as abas do formulário não incluem Campos e Flores.
Selecione a categoria Flores e o formulário será recarregado com essas abas
presentes.

### Aba Natureza

![Aba de natureza do artigo Bluebell](../../../en/images/fields/field-article-bluebell-nature-tab.png)

- **Nome Latim** Este é um campo de entrada de texto, então é apenas uma questão de digitar
  o nome latim da forma de vida que o artigo aborda. No entanto, a categoria
  Natureza cobre a vida em geral, bem como animais ou plantas específicas. Portanto, este
  não é um campo *obrigatório*.
- **Cor** O campo de seleção de cor pode aceitar tanto a entrada de teclado de um
  valor de cor hexadecimal quanto uma cor selecionada a partir da ferramenta de escolha de cores. O número hexadecimal
  é xrrggbb onde rr são valores de vermelho, gg são valores de verde e bb são valores de azul.
  Na saída, o site exibe o valor hexadecimal, o que não é muito útil!

### Aba Flores

![Aba de natureza do artigo Bluebell](../../../en/images/fields/field-article-bluebell-flowers-tab.png)

- **Estação de Floração** O campo de caixa de seleção - bluebells são flores bem conhecidas da primavera,
  então a seleção de uma caixa de seleção é apropriada.
- **Resistência** O campo inteiro. Há um problema aqui - não há método
  disponível para deixar este campo vazio. Portanto, ele está sempre presente na saída,
  mesmo para artigos mais gerais sobre flores, onde não é apropriado. Há uma
  solução alternativa envolvendo uma substituição de modelo.

## Resultado do Site

Dê uma olhada no resultado visto em seu site. Neste exemplo, um item de menu de artigo único foi criado:

![Visualização do site do artigo Bluebell](../../../en/images/fields/field-article-bluebell-site.png)

### A cor em hexadecimal

A exibição padrão dos dados é o valor hexadecimal da cor, que não é muito útil. A solução fácil é criar uma substituição de template para o plugin de campos / cor, que é o que é mostrado na captura de tela acima.

Basta substituir esta linha:
```
echo htmlentities($value);
```
por estas linhas:
```
if (is_array($value)) {
  $list = [];
  foreach ($value as $v) {
    $x = htmlentities($v);
    $list[] = '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
    echo implode(', ', $list);
  }
} else {
    $x = htmlentities($value);
    echo '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
}
```
E o valor hexadecimal será precedido por uma amostra com a cor de fundo do valor.

*Traduzido por openai.com*

