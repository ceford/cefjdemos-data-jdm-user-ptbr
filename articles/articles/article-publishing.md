<!-- Filename: J6.x:_Article_Publishing / Display title: Artigo: Edição - Publicação  -->

## Introdução

Uma parte fundamental de um Sistema de Gerenciamento de Conteúdo (CMS) é sua capacidade de entregar conteúdo a usuários selecionados por períodos determinados. O Joomla! faz isso com níveis de acesso e datas de início e término de publicação.

Datas de início e término podem ser definidas tanto para artigos *Em Destaque* quanto para artigos *Não Destacados*. Por exemplo, um novo artigo pode ser destacado por um período definido, digamos 30 dias, após o qual ele se tornaria um artigo comum não destacado. Ele desapareceria dos layouts de artigos em Destaque, mas ainda apareceria em outros layouts de Blog ou de artigo Único.

Geralmente, os artigos são publicados no dia em que são criados e permanecem assim até serem despublicados, arquivados ou excluídos.

## Captura de Tela

![Aba de publicação do formulário de edição do artigo](../../../en/images/articles/articles-edit-publishing-tab.png)

O painel *Metadados* é explicado em um artigo separado. Este artigo aborda o painel *Publicação*.

## Painel de Publicação

Alguns dos campos no formulário são destinados apenas para informação e não podem ser alterados diretamente no formulário. Eles são exibidos com fundos cinzas. Outros campos podem ser alterados, se necessário.

### Iniciar Publicação

Este campo é definido para a data e hora atuais quando o artigo é salvo pela primeira vez. Se você quiser que o artigo fique embargado até uma data e hora futuras, pode definir seu valor usando a ferramenta de Calendário ou editando diretamente os valores do campo.

### Finalizar Publicação

Por padrão, este campo está em branco. Se desejar que o artigo desapareça após uma data e hora especificadas, use a ferramenta de Calendário ou digite uma data e hora futuras diretamente no campo. Nesse momento, o artigo desaparecerá do site. Na lista de Artigos, ele será marcado como *Publicado, mas Expirado*.

### Iniciar Destaque

Se o artigo for marcado como um *Artigo em Destaque*, este campo pode ser configurado para que ele apareça em um layout de *Artigos em Destaque* na data especificada. Note que a data não será salva se o artigo não estiver marcado como um *Artigo em Destaque*.

### Finalizar Destaque

Se o artigo for marcado como um Artigo em Destaque, este campo pode ser configurado para que ele desapareça de um layout de *Artigos em Destaque* na data especificada. O artigo permanece publicado e ainda pode aparecer em outros layouts. Na lista de Artigos, ele será marcado como *Destacado, mas Expirado*.

### Data de Criação

Esta data é definida quando o artigo é salvo pela primeira vez. Você pode querer alterá-la se tiver criado uma série de artigos em ordem aleatória e desejar classificá-los em ordem de criação.

### Criado Por

O ID do Usuário do criador é salvo no momento da criação e o Nome desse usuário aparece neste campo. Você pode mudar o Criador selecionando o ícone de pessoa para revelar um diálogo pop-up *Selecionar Usuário*, onde você pode encontrar e selecionar um usuário diferente.

### Criado por Apelido

Se você não quiser que o Nome de Usuário do criador apareça no bloco de informações do artigo, pode inserir um Apelido aqui. Insira seu apelido, salve o artigo e veja como ficou com o botão de Pré-visualização na Barra de Ferramentas.

## Programação da Publicação de um Artigo

Por padrão, os artigos são configurados como **Publicado** assim que são salvos. O salvamento inicial do artigo cria a **Data de Criação** e as datas de **Início da Publicação**.

Programar um artigo envolve definir manualmente uma data e hora de **Início da Publicação** para adiar a publicação. Você também pode definir datas e horários para **Término da Publicação**.

**Nota:** Para que a programação funcione, o **Status** do artigo deve ser configurado como **Publicado**.

Antes da data de Início da Publicação, os artigos são considerados como **Pendente** e, após a data de Término da Publicação, são considerados **Expirado**. Apesar de o próprio artigo estar configurado como publicado, o Joomla usa as configurações de início e término para substituir o estado padrão de publicado.

Os valores de data e hora podem ser digitados nos campos de data ou selecionados com a ferramenta de calendário, que é aberta ao selecionar o ícone de calendário no final de cada campo de data.

![Datas de publicação](../../../en/images/articles-access/article-schedule-publishing.png)

O calendário se movimenta entre dias, meses e anos usando as setas do teclado para frente, para trás, para cima e para baixo. O botão **Hoje** define a data atual. O botão **Limpar** limpa a data e hora.

* Selecione a data desejada.
* Defina a hora usando as caixas suspensas.
* Selecione o botão **Fechar** do Calendário para definir a data e hora selecionadas.
* Selecione **Salvar** ou **Salvar & Fechar** na Barra de Ferramentas para salvar as alterações. 

## Ícones da Visualização de Lista

Na lista de Artigos, o ícone de *Destaque* geralmente é um círculo cinza ou uma estrela amarela. Da mesma forma, o ícone de *Status* geralmente é um tique verde ou uma cruz cinza. Cada um possui uma dica de ferramenta (Tooltip) e a ação usual é alternar o estado.

- Publicado e Atual: <span class="icon-publish" aria-hidden="true"></span>
- Não publicado: <span class="icon-unpublish" aria-hidden="true"></span>
- Destacado: <span class="icon-featured" aria-hidden="true"></span>
- Não destacado: <span class="icon-unfeatured" aria-hidden="true"></span>

Os ícones para artigos com datas de início e fim agendadas são diferentes.

- Publicado, mas Pendente: <span class="icon-pending" aria-hidden="true"></span>
- Publicado, mas Expirado: <span class="icon-expired" aria-hidden="true"></span>
- Destacado, mas Pendente: <span class="icon-pending" aria-hidden="true"></span>
- Destacado, mas Expirado: <span class="icon-expired" aria-hidden="true"></span>

Em cada caso, uma dica de ferramenta (Tooltip) mostra informações adicionais sobre as datas agendadas.

## Dicas

- Você também pode agendar a publicação de artigos a partir do front end.
- Também é possível agendar através do item de menu do artigo.
- O agendamento também está disponível para Contatos e Módulos.

*Traduzido por openai.com*

