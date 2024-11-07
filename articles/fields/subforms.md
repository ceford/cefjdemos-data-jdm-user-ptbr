<!-- Filename: jdocmanual?manual=user&heading=fields&filename=subform.md / Display title: Campo de Subformulário -->

## Finalidade

O campo Subform permite que uma seleção de campos seja agrupada em uma lista repetível.

## Criação de Campos

Primeiro, crie os campos necessários no subformulário. No exemplo descrito aqui, há um campo de Calendário (Data de Aquisição), um campo de Texto (Preço) e um campo de Cor (Cor da Flor) para serem usados em uma lista de vários espécimes.

**Erro:** Há um bug no código do campo de Calendário que leva a um erro fatal ao salvar um artigo pela segunda vez. Para evitar esse problema, configure o valor *Mostrar Hora* do campo de Calendário para *Sim*.

Opções especiais para este campo:

- **Título** e **Rótulo**. Neste exemplo, estes estão configurados para *Espécimes*.
- **Campos**. Adicione os campos necessários no subformulário um por um. Cada linha possui uma lista suspensa de campos disponíveis e um alternador de *Renderizar Valores* Sim/Não. A ordem dos itens pode ser alterada com o ícone de arrastar.

![Criação de subformulário](../../../en/images/fields/fields-subform.png "Criação de subformulário")

## Inserção de Dados

No formulário de inserção de dados, você precisa adicionar linhas para cada espécime. Cada linha contém um campo de Calendário, um campo de Texto e um campo de Cor.

![Inserção de dados do subformulário](../../../en/images/fields/fields-subform-entry.png "Inserção de dados do subformulário")

## Exibição de Dados

No artigo, o subformulário intitulado Exemplares possui uma linha para cada exemplar. Procure o item **Exemplares** nesta captura de tela:

![Exibição de todos os campos](../../../en/images/fields/fields-display.png "Exibição de Campos")

*Traduzido por openai.com*

