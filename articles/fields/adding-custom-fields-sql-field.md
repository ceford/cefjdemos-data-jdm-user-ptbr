<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Campo SQL -->

## Finalidade

O campo SQL fornece uma lista suspensa de entradas obtidas a partir de uma consulta ao banco de dados. Para usar este campo, você precisa saber como construir uma consulta e deve testá-la no phpMyAdmin.

## Criação de Campo

As opções especiais dentro deste campo são:

- **Múltiplo** Permitir que múltiplos valores sejam selecionados. Se configurado para *Sim*, a lista exibirá 4 itens. Caso contrário, ela exibirá 1 item. Em ambos os casos, haverá uma longa lista para rolar e fazer seleções - se ativado.
- **Consulta** A consulta SQL que fornecerá os dados para a lista suspensa. A consulta deve retornar duas colunas; uma chamada 'value', que conterá os valores dos itens da lista; a outra chamada 'text', contendo o texto na lista suspensa.

Neste exemplo, uma tabela contendo uma lista de nomes de países é utilizada. Esta é a consulta:
```
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![Criação de Campo SQL](../../../en/images/fields/fields-sql-edit.png)

**Nota:** Neste exemplo, a inclusão do tipo de campo no Título é apenas para fins de demonstração. Deixe-o de fora dos seus próprios títulos de campo.

## Entrada de Dados

Simples - selecione da lista.

![Entrada de dados de campo SQL](../../../en/images/fields/fields-sql-data-entry.png)


## Exibição de Dados

A captura de tela do site a seguir mostra o campo exibido em um artigo. A
opção *Exibição automática* é responsável pela posição do campo e
seu modelo é responsável pelo design do campo.

![Exibição de campo SQL no site](../../../en/images/fields/fields-sql-site.png)

A saída é um único item ou uma lista de itens separados por vírgulas (nomes de países)
seguindo o rótulo do campo (País de Origem).

