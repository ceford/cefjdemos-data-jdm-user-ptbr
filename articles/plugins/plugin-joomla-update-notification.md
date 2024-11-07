<!-- Filename: J3.x:Plugin_Joomla_Update_Notification / Display title: Notificação de Atualização do Joomla! -->

## Ícone e Tarefa

Existem dois plugins com nomes semelhantes:

* **Ícone Rápido - Notificação de Atualização do Joomla!**
* **Tarefa - Notificação de Atualização do Joomla!**

O primeiro verifica se há atualizações do Joomla e notifica você quando visita a página do Painel Inicial. Ele tem um parâmetro: o Grupo deste plugin (este valor é comparado com o valor do grupo usado nos módulos de Ícones Rápidos para injetar ícones).

O segundo verifica periodicamente a disponibilidade de novas versões do Joomla!. Quando uma é encontrada, ele aciona uma tarefa para enviar um e-mail de lembrete de atualização para Super Usuários. O e-mail pode ser personalizado via *Sistema → Modelos de E-mail*.

Os e-mails enviados pelos plugins do Sistema de Notificação de Atualização do Joomla! têm a intenção de ajudar a manter o software atualizado, o que ajuda a manter o site seguro. As atualizações devem ser instaladas o mais rápido possível após o lançamento.

## Status do Plugin

Os dois plugins separados podem estar Ativos ou Desativados.

- Com **Ícone Rápido ... Desativado** o ícone *Verificando Joomla ...* no Painel Inicial permanece inativo, embora você possa selecioná-lo para ir à página de atualização do Joomla.
- Com **Tarefa ... Desativada:** a tarefa de enviar um e-mail não é acionada.

## Parâmetros da Tarefa

No menu do Administrador, vá para **Sistema / Tarefas Agendadas** e selecione o item **Notificação de Atualização** na lista de *Tarefas Agendadas*. Existem várias abas de parâmetros e informações lá para visualizar e alterar, se apropriado.

### Frequência dos E-mails de Notificação

A frequência de execução da tarefa é configurada para 24 horas por padrão. Isso significa que o site Joomla verificará atualizações para o núcleo e todas as extensões, plugins, módulos e templates instalados em intervalos de 24 horas. Um valor de 0 enviaria um e-mail de atualização toda vez que o site fosse acessado. 0 é apenas para testes!

Note que a tarefa é acionada pela atividade do site. Se você for o único usuário, ela será acionada na sua próxima visita, caso esse intervalo seja superior a 24 horas.

### E-mails para Super Usuários

A notificação por e-mail é enviada somente para os usuários que possuem o privilégio de Super Usuário. Este campo permite que você selecione quais Super Usuários receberão as notificações por e-mail.

- Se deixado em branco, todos os Super Usuários do site receberão o e-mail de notificação de atualização.
- Para limitar quais Super Usuários receberão a notificação de atualização, insira aqui os endereços de e-mail dos Super Usuários. Se houver múltiplos endereços de e-mail de Super Usuários, use uma vírgula para separá-los.

### Idioma do E-mail

A notificação pode ser enviada em qualquer idioma que você estiver usando no seu site.

- **Automático (padrão)** envia o e-mail de notificação de atualização no idioma padrão do site.
- Selecionar um idioma diferente de Automático (padrão) força o e-mail de notificação de atualização a ser enviado nesse idioma específico.

## Dicas

- Para desativar as notificações por e-mail de atualização do Joomla!, basta desabilitar o plugin.
- O texto do Assunto e do Corpo do e-mail pode ser modificado através da lista
**Sistema / Modelos de E-mail**. Selecione o item **Joomla: Notificação de Atualização**. Em um site multilíngue, ele estará no idioma atualmente selecionado.
  - **Assunto** Observe que os espaços reservados {SITENAME} – {URL} são substituídos quando a mensagem é enviada.
  - **Corpo** Há mais espaços reservados lá também!

*Traduzido por openai.com*

