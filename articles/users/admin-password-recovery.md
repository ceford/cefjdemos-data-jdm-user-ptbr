<!-- Filename: How_do_you_recover_or_reset_your_admin_password%3F / Display title: Recuperação de Senha do Administrador   -->

## Introdução

Normalmente, um Super Usuário pode adicionar, editar e excluir usuários e senhas da lista de Usuários. Em algumas situações, isso pode não ser possível. Por exemplo, a pessoa que conhecia a senha de um Super Usuário não está mais disponível. Ou talvez o Super Usuário tenha esquecido a senha que foi usada.

Nesses casos, existem dois métodos disponíveis para permitir que um Administrador do site faça login como um Super Usuário.

## Método 1: Editar o Arquivo configuration.php

Se você tiver acesso ao arquivo `configuration.php` da instalação do Joomla no seu servidor, então poderá redefinir a senha de um Super Usuário ou criar um novo Super Usuário se conseguir fazer login como Gerente ou Administrador.

Você precisa abrir o arquivo `configuration.php` em um editor de texto. Primeiro, altere suas permissões de arquivo para 644. Suas ferramentas de gerenciamento de site, como cPanel ou Plesk (existem outras), geralmente permitem que você faça isso online. Caso contrário, pode ser necessário usar FTP para baixar o arquivo, alterá-lo localmente e enviá-lo novamente.

Adicione esta linha no final do arquivo, mas antes da chave de fechamento:
```
    public $root_user='meunome';
```
onde **meunome** é um nome de usuário com acesso ao grupo *Gerente* ou *Administrador* para o qual você conhece a senha. Um nome de usuário que esteja nos grupos *Autor*, *Editor* ou *Publicador* não funcionará porque esses grupos não possuem acesso ao backend.

Este usuário agora será um Super Usuário temporário.

Faça login na área administrativa e altere a senha do Super Usuário para a qual você não tem a senha ou crie uma nova conta de Super Usuário. Se você criar um novo usuário, talvez queira bloquear ou excluir o usuário antigo, dependendo das suas circunstâncias.

Ao terminar, certifique-se de usar o link *Selecionar aqui para tentar fazer isso automaticamente*, que aparece na caixa de alerta, para remover a linha que foi adicionada ao arquivo configuration.php. Se usar o link não for bem-sucedido, então volte e exclua a linha adicionada no seu arquivo configuration.php usando um editor de texto.

Se você não tiver usuários que saibam suas senhas, pode ser necessário fazer uma alteração no seu banco de dados.

## Método 2: Editar o Banco de Dados

Se os métodos acima não funcionaram, você tem duas outras opções, ambas exigindo trabalho diretamente com o banco de dados MySQL.

### Alterar uma Senha no Banco de Dados

A opção mais simples é alterar a senha do Super Usuário no banco de dados para um valor conhecido. Isso requer que você tenha acesso ao banco de dados MySQL usando phpMyAdmin ou outro cliente. Estas instruções mostram como alterar uma senha para a palavra **secret**.

Este método funcionará apenas se o usuário selecionado estiver nos grupos *Manager* ou *Administrator*.

**Certifique-se de mudar a senha do Super Usuário assim que recuperar o acesso!**

1. Abra o phpMyAdmin e selecione o banco de dados do site Joomla!. Isso mostrará as tabelas do banco de dados no lado esquerdo da tela.
2. Encontre e selecione a tabela *#__users* onde *#_* é o prefixo da tabela para o seu site.
3. Na visualização *Browse*, encontre o usuário cuja senha você deseja alterar e selecione o ícone de Editar para essa linha.
   - se a lista for longa, selecione o botão SQL no topo e use esta consulta:<br>
   `SELECT * FROM `xxxxx_users` WHERE `username` = 'username'`<br>
   onde você utiliza o seu prefixo de banco de dados para substituir `xxxxx` e o nome de usuário que você precisa encontrar no lugar de `username`.
4. No formulário de edição, altere a senha para<br>
   `d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199`<br>
   e selecione o botão *Go* na parte inferior do formulário. O phpMyAdmin deve exibir a mensagem *Affected rows: 1*. Neste ponto, a senha deve ser **secret**.
5. Faça login com este usuário e senha e altere a senha deste usuário para um valor seguro. Verifique todos os usuários para garantir que são legítimos. Se você foi invadido, pode querer mudar todas as senhas no site.

### Adicionar um novo Super Usuário

Se alterar a senha não funcionar, ou você não tem certeza de qual usuário é um membro do grupo Super Usuário, você pode usar este método para criar um novo Super Usuário.
1. Abra o phpMyAdmin e selecione o banco de dados do site Joomla!.
2. Selecione o botão *SQL* na barra de ferramentas para executar uma consulta SQL no banco de dados selecionado. Isso exibirá um campo chamado "Run SQL query/queries on database xxxxx".
3. Apague qualquer texto neste campo e copie e cole a seguinte consulta. Lembre-se de substituir `xxxxx` pelo seu próprio prefixo de banco de dados.
    ```
    INSERT INTO `xxxxx_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `xxxxx_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');
    ```
    Selecione o botão *Go* para executar a consulta e adicionar o novo Super Usuário à tabela.

Neste ponto, você deve ser capaz de fazer login no back end do Joomla! com o nome de usuário *admin2* e a senha *secret*.

Depois de fazer login, vá para a lista de Usuários e altere a senha para um novo valor seguro e adicione um endereço de email válido à conta.

Se houver uma chance de que você tenha sido *invadido*, certifique-se de verificar se todos os usuários são legítimos, especialmente quaisquer membros do grupo Super Usuário.

## Senhas Temporárias Alternativas

**Aviso:** Os valores das senhas mostrados nesta página são de conhecimento público e
são apenas para recuperação. Para evitar ser hackeado, certifique-se de alterar uma senha
temporária para um valor seguro após fazer login.

    password = "esta é a senha com hash MD5 e sal"
    ------------------------------------------------------
    admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
    secret = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
    OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm

*Traduzido por openai.com*

