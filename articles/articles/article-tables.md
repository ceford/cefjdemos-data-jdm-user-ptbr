<!-- Filename: J4.x:Article_Tables / Display title: Artigo: Edição - Tabelas  -->

## Sobre Tabelas

Em HTML, tabelas consistem em linhas e colunas de células. Por exemplo, uma
tabela simples pode consistir em 4 linhas e 4 colunas, totalizando 16 células.
No entanto, as células podem ser combinadas horizontalmente ou verticalmente para
criar estruturas de tabela bastante intrincadas. Tabelas também têm recursos
não tão óbvios, como cabeçalho, corpo, rodapé e legendas. As tabelas podem ser
aninhadas!

Por padrão, as células da tabela se expandem para acomodar seu conteúdo. A única
formatação vem da marcação da tabela: por padrão, as células de cabeçalho (`<th>`) têm
texto em negrito e centralizado, enquanto as células de dados (`<td>`) têm texto normal
e alinhado à esquerda.

O uso de tabelas deve ser reservado para dados estritamente tabulares, como um
Cronograma ou um Calendário, onde é importante manter a estrutura de linhas e
colunas. Tabelas não devem ser usadas para layout, como
posicionamento de imagens ou texto lado a lado.

Há mais informações nos seguintes artigos:

- [Noções Básicas de Tabelas](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)
- [Recursos Avançados e Acessibilidade](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced)
- [Estilizando Tabelas](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Styling_tables)

Tabelas são um dilema! Se você inserir uma tabela usando as ferramentas de tabela do TinyMCE,
a tabela parecerá boa na tela de edição e no site, mas o layout é
alcançado com estilos CSS embutidos, que podem ser volumosos e difíceis de editar.
Se a tabela for inserida como HTML puro, o resultado não parece bom no
editor de texto TinyMCE, mas pode tirar proveito das classes Bootstrap e parecer
muito melhor no site. Ambos os métodos são abordados abaixo.

## Inserir uma Tabela com as Ferramentas do TinyMCE

Para começar a trabalhar com uma tabela:

- Abra o artigo que deseja editar.
- Coloque o cursor em uma linha em branco onde a tabela deve aparecer.
- Selecione o botão *Tabela* na primeira linha das ferramentas do TinyMCE.
- No menu suspenso, selecione Tabela e, em seguida, mova o cursor para definir o
  número de linhas e colunas. As setas do teclado também funcionam para isso.
- Selecione a última célula na matriz 4x4.
- Preencha as células da tabela.

Opções de edição:

- Você pode inserir uma linha acima ou abaixo de uma célula selecionada.
- Você pode inserir uma coluna antes ou depois de uma célula selecionada.
- Você pode excluir uma linha ou coluna.
- Você pode arrastar as bordas das colunas para mudar as larguras ou alturas das colunas.
- Você pode mesclar células - arraste sobre as células para selecioná-las e depois
  use Tabela -> Célula -> Mesclar células.
- Você pode selecionar as Propriedades da Tabela, incluindo largura da borda, estilo e cor, e
  cor de fundo.

Se você usar o botão Alternar Editor, verá que o layout é alcançado com
declarações de estilo inline em cada linha e em cada célula. Aqui está um curto exemplo:

```html
<table style="border-collapse: collapse; width: 100%; height: 96px;" border="1"><colgroup><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"></colgroup>
<tbody>
<tr style="height: 24px;">
<td style="height: 24px;">Dia</td>
<td style="height: 24px;">Manhã</td>
<td style="height: 24px;">Tarde</td>
<td style="height: 24px;">Noite</td>
</tr>
<tr style="height: 24px;">
<td style="height: 24px;">Terça-feira</td>
<td style="height: 24px;">Recepção</td>
<td style="height: 24px;">Apresentações</td>
<td style="height: 24px;">Churrasco</td>
</tr>
...
</tbody>
</table>
```

## Inserir uma Tabela como HTML

Se preferir, você pode dispensar os estilos inline e usar classes do Bootstrap. Você precisaria modificar a tabela criada pelas ferramentas de Tabela do TinyMCE ou digitá-la manualmente. Ficaria assim:

```html
<div class="table-responsive">
<table class="table table-striped table-bordered table-group-divider">
<thead>
<tr>
<th>Dia</th>
<th>Manhã</th>
<th>Tarde</th>
<th>Noite</th>
</tr>
</thead>
<tbody class="table-group-divider">
<tr>
<th>Terça-feira</th>
<td>Boas-vindas</td>
<td>Apresentações</td>
<td>Churrasco</td>
</tr>
...
</tbody>
</table>
</div>
```

Aqui, as classes do Bootstrap têm os seguintes efeitos:

- `table` - aplica vários estilos para dar um layout de tabela padrão agradável.
- `table-striped` - as linhas alternadas são escuras e claras.
- `table-bordered` - aplica bordas às células.
- `table-group-divider` - aplica uma linha em negrito acima de um elemento.
- `table-responsive` - permite que uma tabela larga role para a direita e esquerda.

A captura de tela do site a seguir mostra uma tabela para um programa de conferência com os estilos inline padrão do TinyMCE e uma tabela semelhante com estilos Bootstrap:

![Exemplo de tabelas](../../../en/images/articles/articles-site-tables.png)

Consulte a documentação do Bootstrap sobre [Tabelas](https://getbootstrap.com/docs/5.3/content/tables/) para mais opções.

## Consideração

Você pode colocar o HTML para uma tabela em um módulo personalizado e incluir esse módulo no artigo. No artigo, isso aparecerá como `{loadmoduleid xx}`, onde xx é o ID do módulo.

*Traduzido por openai.com*

