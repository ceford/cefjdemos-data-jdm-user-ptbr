<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Campo de Calendário -->

## Finalidade

O campo de Calendário fornece uma caixa de texto para a inserção de uma data. Um ícone ao lado da caixa de texto chama um seletor de calendário pop-up, que pode ser usado para selecionar uma data de um calendário gráfico.

## Criação de Campo

Os parâmetros comuns de campo são descritos em um artigo separado.

* **Título** Você pode ter vários campos de data em um artigo, portanto, é necessário cuidado ao definir o título para evitar ambiguidades na saída.
* **Rótulo** Este é o que é exibido na saída. Se deixado em branco, ele é definido a partir do conteúdo do campo Título, mas pode ser alterado.
* **Mostrar Hora** Se configurado como *Sim*, a hora é adicionada ao campo de data, ao seletor de data e à data de saída. **Cuidado**: Mesmo que você não especifique a hora na data padrão, ela será exibida quando a opção *Mostrar hora* estiver ativa.
* **Placeholder** Este está na aba Opções. Ele pode ser configurado para um formato de data, como *YYYY-MM-DD*, para lembrar os usuários do formato necessário e/ou um lembrete do que a data representa, como *Data de chegada*.

![criação de campo de calendário](../../../en/images/fields/fields-calendar-edit.png)

**Nota:** Neste exemplo, a inclusão do tipo de campo no Título é apenas para fins de demonstração. Deixe de fora nos títulos dos seus próprios campos.

## Entrada de Dados

O uso do campo de Calendário é simples. Você pode digitar a data no formato necessário ou selecionar uma data utilizando o seletor de datas. Cuidado é necessário ao digitar datas. Um erro na data é corrigido ao salvar para uma nova data. Por exemplo, uma data de 2024-14-02 é corrigida para 2025-02-02.

A captura de tela a seguir mostra uma data de Aquisição:

![entrada de dados do campo de calendário](../../../en/images/fields/fields-calendar-data-entry.png)

Os campos só aparecem em um artigo se forem preenchidos no formulário de entrada de dados do artigo.

## Exibição de Dados

A captura de tela a seguir do site mostra o campo exibido em um artigo. A opção *Exibição automática* é responsável pela posição do campo e seu modelo é responsável pelo design do campo.

![exibição do campo de calendário no site](../../../en/images/fields/fields-calendar-site.png)

Os formatos de data são localizados usando strings de idioma.

*Traduzido por openai.com*

