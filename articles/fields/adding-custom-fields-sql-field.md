<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Campo SQL -->

## Finalidade

O campo SQL fornece uma lista suspensa de entradas obtidas a partir de uma consulta ao banco de dados. Para usar este campo, você precisa saber como construir uma consulta e deve testá-la no phpMyAdmin.

## Criação de Campo

As opções especiais dentro deste campo são:

- **Múltiplo** Permitir que múltiplos valores sejam selecionados. Se configurado como *Sim*, a lista exibe 4 itens. Caso contrário, exibe 1 item. Em ambos os casos, há uma longa lista para percorrer ao fazer seleções - se ativada.
- **Consulta** A consulta SQL que fornecerá os dados para a lista suspensa. A consulta deve retornar duas colunas; uma chamada 'value', que conterá os valores dos itens da lista; e outra chamada 'text', contendo o texto na lista suspensa.

Neste exemplo, uma tabela contendo uma lista de nomes de países é usada. Esta é a consulta:
```sql
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![Campo SQL](../../../en/images/fields/fields-sql.png "Campo SQL")

## Entrada de Dados

Simples - selecione da lista.


## Exibição de Dados

A captura de tela do Site a seguir mostra o campo exibido em um artigo. A opção *Exibição automática* é responsável pela posição do campo, e seu template é responsável pelo design do campo.

Procure o item **País de Origem**.

![Exibição de todos os campos](../../../en/images/fields/fields-display.png "Exibição dos campos")

A saída é um único item ou uma lista de itens separados por vírgula (nomes de países) seguindo o rótulo do Campo (País de Origem).

