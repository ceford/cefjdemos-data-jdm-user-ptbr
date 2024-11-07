<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Campo de Cor -->

## Finalidade

O campo de Cor fornece um seletor para a seleção visual de uma cor. O campo mostra o valor hexadecimal resultante.

## Criação de Campos

Opções especiais para este campo:

- **Classe do Campo** Defina como *w-auto* para que o campo tenha apenas a largura necessária para a amostra e o valor.

## Entrada de Dados

Você pode digitar um valor de cor hexadecimal se souber que os números hexadecimais variam de 0 a 9 e depois de a a f, e os pares de números representam vermelho, verde e azul. Então, #00ff00 significa sem vermelho, máximo de verde e sem azul. Ou você pode usar um cursor para selecionar uma cor visualmente.

![Seletor de Cores](../../../en/images/fields/fields-colour-entry.png "Seletor de Cores")

## Exibição de Dados

A captura de tela do Site a seguir mostra o campo exibido em um artigo. A opção *Exibição automática* é responsável pela posição do campo, e o seu template é responsável pelo design do campo.

A exibição padrão dos dados é o valor de cor em hexadecimal, que não tem muita utilidade. A solução fácil é criar uma substituição de template para os campos / plugin de cor. Basta substituir esta linha:
```
echo htmlentities($value);
```
por estas linhas:
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
E o valor hexadecimal será precedido por uma amostra com a cor de fundo do valor.

Procure pelo item **Cor da Flor**.

![Exibição de todos os campos](../../../en/images/fields/fields-display.png "Exibição de Campos")

