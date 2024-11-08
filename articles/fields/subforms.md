<!-- Filename: jdocmanual?manual=user&heading=fields&filename=subform.md / Display title: Campo de Subformulário -->

## Finalidade

O Campo de Subformulário permite que uma seleção de campos seja agrupada em uma lista repetível.

## Criação de Campo

Primeiro, crie os campos necessários no subformulário. No exemplo descrito aqui, há um campo de Calendário (Data de Aquisição), um campo de Texto (Preço) e um campo de Cor (Cor da Flor) para ser utilizado em uma lista de vários espécimes.

**Erro:** Existe um erro no código do campo de Calendário que leva a um erro fatal ao salvar um artigo pela segunda vez. Para evitar esse problema, ajuste o valor *Mostrar Hora* do campo de Calendário para *Sim*.

Opções especiais para este campo:

- **Título** e **Rótulo**. Neste exemplo, estes são configurados como *Espécimes*.
- **Campos**. Adicione os campos necessários no subformulário um por um. Cada linha tem uma lista suspensa de campos disponíveis e uma opção alternável de Renderizar Valores Sim/Não. A ordem dos itens pode ser alterada com o ícone de arrastar.

![Criação de Subformulário](../../../en/images/fields/fields-subform-edit.png)

**Nota:** Neste exemplo, a inclusão do tipo de campo no Título é apenas para fins de demonstração. Deixe-o de fora nos títulos dos seus campos.

## Entrada de Dados

No formulário de entrada de dados, você precisa adicionar linhas para cada espécime. Cada linha contém um campo de Calendário, um campo de Texto e um campo de Cor.

![Entrada de dados em subformulário](../../../en/images/fields/fields-subform-data-entry.png)

## Exibição de Dados

No artigo, o subformulário intitulado Especímenes tem uma linha para cada espécime. Procure o item **Especímenes** nesta captura de tela:

![exibição do subformulário no site](../../../en/images/fields/fields-subform-site.png)

*Traduzido por openai.com*

