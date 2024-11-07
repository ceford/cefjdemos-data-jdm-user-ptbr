<!-- Filename: J4.x:Privacy_Workflow / Display title: Fluxo de Trabalho de Privacidade -->

## Criando uma Solicitação

O processamento de solicitações de informações pessoais é o principal objetivo do componente de privacidade. Os usuários podem pedir um resumo de seus dados pessoais ou solicitar que todos os seus dados sejam removidos. Uma solicitação pode ser criada por um usuário autenticado através do formulário de solicitação ou por um super usuário.

Nesse contexto, um usuário significa qualquer indivíduo ou organização que fez uma solicitação, independentemente de haver ou não uma conta de usuário registrada. Por exemplo, solicitações podem chegar ao administrador do site de pessoas ou organizações que foram adicionadas ao site como contatos.

Os dados pessoais são baseados em endereços de e-mail e o processamento automatizado é limitado a extensões que relatam capacidades de privacidade.

*IMPORTANTE* Para criar e processar solicitações de informações, seu site DEVE ser capaz de enviar e-mails devido à necessidade do proprietário das informações confirmar a solicitação.

### Solicitação de Usuário Autenticado

Usuários registrados podem enviar uma solicitação de informações através de um link de menu de *Solicitação de Informações de Privacidade* disponível apenas após o login. Um bom lugar para esse link é no mesmo menu onde há um link para a **Política de Privacidade** do site. Um Menu Inferior no rodapé do site é frequentemente uma localização preferida. Ao enviar uma solicitação de informações, o usuário deve fornecer:

- O tipo de solicitação: Exportar ou Remover selecionado na lista suspensa.

![fluxo de privacidade solicitação de usuário](../../../en/images/privacy/privacy-workflow-user-request.png)

Ao enviar, uma mensagem indicará que a solicitação foi aceita e um e-mail de verificação está a caminho:

![fluxo de privacidade solicitação de usuário aceita](../../../en/images/privacy/privacy-workflow-user-request-accepted.png)

ou que *Sua solicitação de informações não pôde ser criada. Já existe uma solicitação ativa de informações para este endereço de e-mail e tipo de solicitação. Por favor, contate o proprietário do site para atualizações sobre esta solicitação.*

### Criação por Super Usuário

Através da página **Privacidade: Solicitações de Informações**, qualquer super usuário pode criar uma nova solicitação de informações. Esta é a única maneira de criar solicitações de informações para usuários que NÃO têm contas no site. Para criar uma solicitação:

- Selecione **Usuários → Privacidade → Solicitações** no menu do Administrador.
- Selecione o botão **Novo** na Barra de Ferramentas.
- No campo **E-mail** insira o endereço de e-mail do usuário.
- No campo **Tipo de Solicitação** selecione Exportar ou Remover na lista suspensa.
- **Salvar & Fechar**.

Uma vez criada, a solicitação não pode ser editada. Ela pode apenas ser Invalidada ou Processada.

## Confirmando uma Solicitação

Uma vez que uma solicitação tenha sido criada, independentemente de como ela foi criada, o usuário receberá um e-mail contendo um link para um formulário de confirmação.

![fluxo de trabalho de privacidade confirmar solicitação do usuário](../../../en/images/privacy/privacy-workflow-user-request-confirm.png)

O usuário deve inserir o token fornecido no e-mail e enviar o formulário. O token é válido por 24 horas. Se uma solicitação não for confirmada nesse período, ela será marcada como **Inválida** na lista de Solicitações de Privacidade, e uma nova solicitação deverá ser enviada.

Assim que o usuário confirmar a solicitação, um e-mail será enviado para os Super Usuários para indicar que uma ação é necessária.

- No menu do Administrador, selecione **Usuários → Privacidade → Solicitações**.
- Solicitações que requerem ação serão marcadas como **Confirmadas**.

![fluxo de trabalho de privacidade lista de solicitações de informações](../../../en/images/privacy/privacy-workflow-information-requests-list.png)

## Processando um Pedido de Exportação

Uma vez que um pedido de exportação tenha sido confirmado, há duas ações
disponíveis para superusuários.

- Exportar Dados: Isso reunirá todos os dados relacionados ao assunto do pedido de informações e criará um arquivo XML que será baixado para o seu computador. Isso é útil para permitir que os proprietários do site revisem a exportação de dados antes de enviá-la ao usuário.
- Enviar Exportação de Dados por Email: Isso reunirá todos os dados relacionados ao assunto do pedido de informações, criará um arquivo XML (o mesmo gerado pela ação Exportar Dados) e enviará um email para o usuário com o arquivo de dados exportado anexo.

**Importante:** A ação de exportação só pode coletar dados de extensões
que possuem suporte à privacidade. Portanto, o superusuário que está agindo conforme o pedido deve revisar a exportação e, se necessário, incluir dados contidos em extensões que armazenam dados pessoais mas não possuem suporte à privacidade.

## Processando um Pedido de Remoção

Uma vez que um pedido de remoção é confirmado, há apenas uma ação
disponível para superusuários.

- Excluir Dados: Este processo irá anonimizar e/ou remover dados
  relacionados ao titular da informação. Para pedidos onde o proprietário
  da informação também possui uma conta de usuário registrada, este
  processo irá anonimizar o nome, nome de usuário e endereço de e-mail da
  conta, bem como bloquear o acesso à conta e desconectar o usuário do site
  caso ele esteja conectado no momento em que o pedido é processado.

**Importante:** A ação de exclusão só pode coletar dados de extensões
que têm suporte à privacidade. Portanto, o superusuário que está agindo
sobre o pedido deve revisar a exportação e, se necessário, anonimizar ou
remover manualmente os dados contidos em extensões que armazenam dados
pessoais, mas não têm suporte à privacidade.

Ao selecionar o botão **Excluir Dados** há uma mensagem de confirmação
**Dados Removidos**, mas a lista de Solicitações de Informação: Privacidade
permanecerá inalterada. Os dados do usuário são removidos ou anonimizados,
mas não os dados nas tabelas \#\_\_action_logs, \#\_\_messages e
\#\_\_privacy_requests (veja abaixo).

## Concluindo uma Solicitação

Após o processamento da solicitação, ela deve ser marcada como concluída. Isso indicará que a solicitação foi atendida e não há mais ações a serem realizadas.

- Na lista **Privacidade: Solicitações de Informação**, selecione o endereço de e-mail da solicitação em processamento.
- No formulário **Privacidade: Revisar Solicitação de Informação**:
  - Revise os dados.
  - Selecione o botão apropriado **Exportar**, **Email** ou **Excluir** na Barra de Ferramentas, caso isso ainda não tenha sido feito na visualização de lista.
- Selecione o botão **Concluir** na Barra de Ferramentas (ou o botão **Invalidar** se for considerado uma solicitação inválida).

![fluxo de trabalho de privacidade revisar solicitação de informação](../../../en/images/privacy/privacy-workflow-review-information-request.png)

## Finalmente

Para remover os dados do Log de Ações do Usuário:

- Selecione **Usuários → Log de Ações do Usuário** no menu do Administrador.
- Procure o nome de usuário ou o endereço de e-mail do usuário deletado.
- Selecione a caixa de seleção **Marcar Todos os Itens**.
- Selecione o botão **Excluir** na Barra de Ferramentas.

Para remover dados de Mensagens Privadas e dados de Solicitações de Privacidade:

- Não há uma maneira fácil de remover em massa nenhum desses tipos de dados
  dentro do Joomla. O método mais rápido é procurar o Nome de Usuário
  (endereço de e-mail) no banco de dados com o phpMyAdmin e excluir os registros
  lá. Aqui está um exemplo de captura de tela:

![fluxo de trabalho de privacidade delete com phpmyadmin](../../../en/images/privacy/privacy-workflow-delete-with-phpmyadmin.png)

## Recursos Adicionais

- [Guia do Desenvolvedor para o Conjunto de Ferramentas de Privacidade](https://docs.joomla.org/Special:MyLanguage/J3.x:Integrate_Extensions_with_the_Privacy_Component)

*Traduzido por openai.com*

