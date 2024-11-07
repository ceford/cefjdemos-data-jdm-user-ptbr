<!-- Filename: Unable_to_connect_to_the_database / Display title: Conexão com o Banco de Dados  -->

## Erro de Conexão

Se você receber um erro de "**Incapaz de conectar ao banco de dados**" durante a instalação, verifique se inseriu corretamente os detalhes do seu banco de dados MySQL/MariaDB. O script de **instalação** não permitirá que você continue a menos que os detalhes estejam corretos.

Observe que não se espera que você crie um usuário e senha de banco de dados durante a instalação. Eles devem ser criados antecipadamente.

Se o erro ocorrer após mover seu site para outro host, verifique os seguintes itens do arquivo *configuration.php*. As configurações normais do banco de dados são as seguintes:

```php
public $dbtype = 'mysqli';
public $host = 'localhost';
public $user = 'seuusuariobd';
public $password = 'suasenhabd';
public $db = 'seubancodados';
public $dbprefix = 't6q6i_';
```

Se o erro ocorrer em um site que já estava funcionando, existem várias possíveis razões, às vezes temporárias e às vezes acidentais.

## As Falhas Mais Comuns

1. Às vezes, você verá esta mensagem se o MySQL/MariaDB tiver parado de funcionar no seu servidor. O administrador do servidor pode desligar temporariamente o MySQL/MariaDB para realizar manutenção. Nessas circunstâncias, é provável que seu site volte a funcionar em breve.
2. Seu usuário de banco de dados foi excluído. Se for esse o caso, você precisará recriar seu usuário de banco de dados com o mesmo nome de usuário e senha que existiam quando você instalou o Joomla pela primeira vez. Use o painel de controle do seu domínio para administrar isso ou entre em contato com o administrador do seu servidor.
3. O nome de usuário ou a senha do seu banco de dados foram alterados.

*Traduzido por openai.com*  

