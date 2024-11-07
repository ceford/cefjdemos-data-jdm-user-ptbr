<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Campo de Calendário -->

## Finalidade

O campo Calendário oferece uma caixa de texto para a inserção de uma data. Um ícone ao lado da caixa de texto exibe um seletor de calendário pop-up, que pode ser usado para selecionar uma data em um calendário gráfico.

## Criação de Campo

Os parâmetros comuns de campo são descritos em um artigo separado.

* **Título** Você pode ter vários campos de data em um artigo, por isso é necessário cuidado ao definir o título para evitar ambiguidades no resultado.
* **Rótulo** Isso é o que é exibido no resultado. Se deixado vazio, é definido a partir do conteúdo do campo Título, mas pode ser alterado.
* **Mostrar Hora** Se configurado para *Sim*, a hora é adicionada ao campo de data, ao seletor de data e à data de saída. **Atenção**: Mesmo que você não especifique a hora na data padrão, a hora será exibida quando a opção *Mostrar hora* estiver ativa.
* **Placeholder** Pode ser definido em um formato de data como *AAAA-MM-DD* para lembrar os usuários do formato necessário e/ou lembrar para que a data serve, como *Data de chegada*.

## Entrada de Dados

O uso do campo de Calendário é simples. Você pode digitar a data no formato exigido ou selecionar uma data usando o seletor de data. É necessário ter cuidado ao digitar datas. Um erro na data é corrigido ao salvar para uma nova data. Por exemplo, uma data de 2024-14-02 é corrigida para 2025-02-02.

A captura de tela a seguir mostra uma data de Aquisição:

![entrada de data de aquisição](../../../en/images/fields/fields-date-entry.png "Data de Aquisição")

Os campos só aparecem em um artigo se forem preenchidos no formulário de entrada de dados do artigo.


## Exibição de Dados

A captura de tela a seguir do Site mostra o campo exibido em um artigo. A opção *Exibição automática* é responsável pela posição do campo e seu template é responsável pelo design do campo.

Procure o item **Data de Aquisição**.

![Exibição de todos os campos](../../../en/images/fields/fields-display.png "Exibição dos campos")

Os formatos de data são localizados usando strings de idioma.

*Traduzido por openai.com*

