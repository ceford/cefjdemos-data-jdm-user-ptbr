<!-- Filename: J4.x:User_Actions_Log / Display title: Registro de Ações do Usuário  -->

## Introdução

O componente de Registro de Ações do Usuário (com_actionlogs) fornece uma infraestrutura para criar um registro de auditoria das atividades do site. As ações que são registradas podem ser ajustadas pelo administrador do site. Extensões de terceiros podem se integrar ao componente para adicionar mensagens personalizadas ou permitir que o sistema processe ações padrão do administrador.

**Nota:** Apenas Super Usuários têm acesso ao componente de Registro de Ações do Usuário.

## Registro de Ações do Usuário

Para visualizar a lista de Registro de Ações do Usuário:

- Selecione **Usuários → Registro de Ações do Usuário** no menu do Administrador.

![página da lista de registro de ações do usuário](../../../en/images/users/user-actions-log-list.png)

Nesta página, um Super Usuário tem uma visão global de todas as atividades dos usuários realizadas em um site.

- Exportar Selecionados como CSV: este botão exporta apenas os itens selecionados na lista visível.
- Exportar Todos como CSV: este botão exporta todos os registros. Os filtros são ignorados.
- Excluir: este botão exclui os itens selecionados.
- Limpar Registro: este botão exclui todas as entradas do registro.
- Opções: um formulário de configuração para definir as opções de registro.

## Opções

O formulário de Opções do Registro de Ações do Usuário permite que o Superusuário selecione quais eventos registrar e se deve incluir endereços IP nos dados de registro.

![página de opções do registro de ações do usuário](../../../en/images/users/user-actions-log-options.png)

## Plugins

O sistema de registro de ações utiliza vários plugins:

### Registro de Ação - Joomla

Quando ativado, este plugin registra as ações principais dos usuários, incluindo ações como login/logout, atualização de artigo, adição de módulo. O plugin não possui parâmetros.

### Sistema - Registro de Ações do Usuário

Quando ativado, este plugin define o número de dias após os quais os registros serão excluídos. Um valor de zero significa que os registros nunca serão excluídos automaticamente.

### Privacidade - Registros de Ações

Quando ativado, este plugin exporta os dados do registro de ações para uma solicitação de privacidade do usuário.

## Módulo de Ações Recentes

Este módulo é exibido apenas para Super Usuários no Painel Inicial.

![módulo de registro de ações do usuário](../../../en/images/users/user-actions-log-module.png)

## Como conectar uma extensão ao sistema

Sinta-se à vontade para editar esta seção, melhorando ou corrigindo-a.

### Script de Instalação de Componente

Adicione a extensão à tabela (`#__action_logs_extensions`) para que ela apareça na configuração dos Logs de Ações do Usuário.
```php
            $extension = 'com_mycomponent';
            $db = Factory::getDbo();
            $db->setQuery(' INSERT into #__action_logs_extensions (extension) VALUES ('.$db->Quote($extension).') ' );
            try {
                // Se falhar, lançará uma RuntimeException
                $result = $db->execute();
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Adicione a configuração da extensão à tabela (`#__action_log_config`) para que os dados das suas ações sejam capturados.
```php
           $logConf = new stdClass();
            $logConf->id = 0;
            $logConf->type_title = 'transaction';
            $logConf->type_alias = $extension;
            $logConf->id_holder = 'id';
            $logConf->title_holder = 'trans_desc';
            $logConf->table_name = '#__mycomponent_transaction';
            $logConf->text_prefix = 'COM_MYCOMPONENT_TRANSACTION';

            try {
                // Se falhar, lançará uma RuntimeException
                // Insira o objeto na tabela.
                $result = Factory::getDbo()->insertObject('#__action_log_config', $logConf);
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Claro que seria melhor realizar alguma verificação para garantir que o registro não exista anteriormente.

### Helper do Componente

Neste exemplo, o helper do componente é usado para executar o armazenamento de ações.
```php
       /**
         * Registra detalhes da transação no registro de log
         * @param   object  $user    Evita obter o usuário atual novamente.
         * @param   int     $tran_id  O ID da transação que acabou de ser criada ou atualizada
         * @param   int     $id  ID passado como referência do formulário para identificar se é um novo registro
         * @return  boolean True
         */
        public static function recordActionLog($user = null, $tran_id = 0, $id = 0)
        {
                // obtém os detalhes do componente como o ID
            $extension =  MycomponentHelper::getExtensionDetails('com_mycomponent');
            // obtém os detalhes da transação para uso no log para fácil referência
            $tran = MycomponentHelper::getTransaction($tran_id);
            $con_type = "transaction";
            if ($id === 0) { $type = 'New '; } else { $type = 'Update '; }

            $message = array();
            $message['action'] = $con_type;
            $message['type'] = $type . $tran->tran_type . ' - '.$tran->tran_desc . ' $' . $tran->tran_amount;
            $message['id'] = $tran->id;
            $message['title'] = $extension->name;
            $message['extension_name'] = $extension->name;
            $message['itemlink'] = "index.php?option=com_mycomponent&task=transaction.edit&id=".$tran->id;
            $message['userid'] = $user->id;
            $message['username'] = $user->username;
            $message['accountlink'] = "index.php?option=com_users&task=user.edit&id=".$user->id;

            $messages = array($message);

            $messageLanguageKey = Text::_('COM_MYCOMPONENT_TRANSACTION_LINK');
            $context = $extension->name.'.'.$con_type;

            $fmodel = MycomponentHelper::getForeignModel('Actionlog', 'ActionlogsModel');

            $fmodel->addLog($messages, $messageLanguageKey, $context, $user->id);

            return true;
        }

        /**
         * Obtém o Modelo de outro componente para uso
         * @param   string  $name    O nome do modelo. Opcional. Padrão para meu próprio por segurança.
         * @param   string  $prefix  O prefixo da classe. Opcional
         * @param   array   $config  Matriz de configuração para o modelo. Opcional
         * @return object   O modelo
         */
        public function getForeignModel($name = 'Transaction', $prefix = 'MycomponentModel', $config = array('ignore_request' => true))
        {
            \Joomla\CMS\MVC\Model\ItemModel::addIncludePath(JPATH_ADMINISTRATOR . '/components/com_actionlogs/models', 'ActionlogsModelActionlog');
            $fmodel = \Joomla\CMS\MVC\Model\ItemModel::getInstance($name, $prefix, $config);

            return $fmodel;
        }
```
### Formulário de Transação no Frontend

Agora que as fundações estão estabelecidas, só precisamos acionar o processo.
Estamos capturando informações sobre uma transação que é criada ou
atualizada e temos um modelo chamado `transactionform.php`. É no
método Save que queremos capturar um log.
```php
       // Assim, o código acima deste ponto faz suas verificações e realiza o que deve ser feito e então, após o salvamento bem-sucedido do registro, verificamos a configuração do parâmetro para ver se é necessário registrar o log, passamos os elementos-chave para o recordActionLog.
            $table = $this->getTable();

            if ($table->save($data) === true) {

                /* ---------------------------------------------------------------- */
                // dispara o log de transação se necessário
                $act_log = $params->get('act_log', 0);
                if ($act_log && $table->id) {
                    // reúne informações e registra em um novo registro de log de ação
                    MycomponentHelper::recordActionLog($user, $table->id, $data['id']);
                }
                /* ---------------------------------------------------------------- */

                return $table->id;
            } else {
                return false;
            }
```
### Arquivo de Idioma

Finalmente, para auxiliar na Listagem de Logs de Ações no lado
administrativo do Joomla, queremos configurar alguns
elementos-chave de dados para serem exibidos no arquivo de idioma en-GB/com_mycomponent.ini.
```ini
    COM_MYCOMPONENT_TRANSACTION_LINK="Usuário {username} criou uma transação ( {type} )"
```

*Traduzido por openai.com*

