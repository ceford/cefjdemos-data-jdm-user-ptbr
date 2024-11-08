<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Campo de Cor -->

## Finalidade

O campo de Cor oferece um seletor para a seleção visual de uma cor. O campo exibe o valor hexadecimal resultante.

## Criação de Campo

Opções especiais para este campo:

- **Classe do Campo** Defina como *w-auto* para tornar o campo apenas largo o suficiente para a amostra e valor.

![Criação de campo de cor](../../../en/images/fields/fields-colour-edit.png)

**Nota:** Neste exemplo, a inclusão do tipo de campo no Título é apenas para fins de demonstração. Deixe-o de fora em seus próprios títulos de campo.


## Entrada de Dados

Você pode digitar um valor de cor hexadecimal se souber que os números hexadecimais variam de 0 a 9 e depois de a a f, e os pares de números são vermelho, verde e azul. Então, #00ff00 é sem vermelho, máximo de verde e sem azul. Ou você pode usar um cursor para selecionar uma cor visualmente.

![Entrada de dados de campo de cor](../../../en/images/fields/fields-colour-data-entry.png)


## Exibição de Dados

A captura de tela do Site a seguir mostra o campo exibido em um artigo. A opção *Exibição automática* é responsável pela posição do campo e seu template é responsável pelo design do campo.

A exibição de dados padrão é o valor da cor em hexadecimal, o que não é muito útil. A solução fácil é criar uma substituição de template para os campos / plugin de cor. Basta substituir esta linha:
```
echo htmlentities($value);
```
por estas linhas:
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
E o valor hexadecimal será precedido por uma amostra com a cor de fundo do valor.

Procure o item **Cor da Flor**.

![exibição do campo de cor no site](../../../en/images/fields/fields-colour-site.png)

