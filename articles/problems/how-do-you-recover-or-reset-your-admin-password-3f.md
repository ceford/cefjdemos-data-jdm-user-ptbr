<!-- Filename: How_do_you_recover_or_reset_your_admin_password%3F / Display title: Como recuperar ou recriar sua senha de administrador? -->

Recuperação da senha do Joomla! 1.5

Esta página é somente para a versão Joomla! 2.5 e posteriores. Se você
ainda usa Joomla! 1.5   instruções podem ser encontradas
aqui.

Normalmente, pode-se criar, editar e apagar usuários e senhas dentro do
Gerenciador de Usuário no Administrativo. Você deve acessar o sistema
com nível de acesso Super User.

Em algumas situações, isso pode não ser possível. Por exemplo, seu site
foi hackeado e as senhas e usuários foram mudados. Ou talvez a pessoa
que sabia as senhas não está mais disponível. Ou ainda você esqueceu a
senha que era usada.

Nesses casos, ainda é possível alterar o banco de dados do Joomla! para
que você possa voltar a acessar como Super User. Esses são os métodos
disponíveis.

## Método 1: arquivo configuration.php

Se você tem acesso ao arquivo configuration.php de sua instalação Joomla
no servidor, é possível recuperar a senha usando o método a seguir.

1\. Usando um programa de FTP, conecte-se ao seu site. Encontre o
arquivo configuration.php e veja as permissões do arquivo. Se estiver em
444 ou outro valor, mude para 644. Isso evitará erros quando fizer o
upload do arquivo alterado seguindo esse procedimento.

2\. Baixe o arquivo de configuração.

3\. Abra o arquivo configuration.php em editor de texto como Notepad++
ou SublimeText e adicione essa linha

    public $root_user='myname';

no fim do arquivo onde myname é um nome de usuário com acesso de
administrador e que você saiba a senha. Um usuário com nível de acesso
Autor ou superior também pode ser usado aqui.

4\. Salve o arquivo configuration.php e suba ele de volta para o site.
Deixe as permissões do arquivo em 644.

Esse usuário será agora um Super User temporário.

5\. Acesse o Painel de Administração e mude a senha do usuário
administrador ou crie um novo usuário Super User. Se criar um novo
usuário, sugerimos bloquear ou apagar o usuário anterior, dependendo das
circunstâncias.

6\. Ao terminar, certifique-se de usar o link "Clique aqui para tentar
fazer automaticamente" que aparece na caixa de alerta para remover a
linha que foi adicionada ao arquivos configuration.php. Se não tiver
êxito usando o link, volta e apague a linha adicionada usando um editor
de texto e suba de volta o arquivo para o site.

7\. Pelo programa de FTP verifique a permissão do arquivo
configuration.php, que deve estar 444. Se você removeu manualmente a
linha adicionada, mude a permissão para 444.

Se você não tem usuários que saibam suas senha e não puder usar o
registro do próprio site, você precisará fazer uma mudança no seu banco
de dados, como mostrado a seguir.

## Método 2: Edição direta no Banco de Dados

Se o método anterior não funcionou, existem mais duas opções. Ambas
exigem mexer diretamente no banco de dados MySQL.

### Mudar a senha no Banco de Dados

Se o usuário Administrador ainda estiver ativo, a opção mais simples é
mudar a senha no banco de dados. Isso exige que se tenha acesso ao banco
de dados MySQL usando phpMyAdmin ou outro cliente.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Mude sua senha assim que voltar a ter
acesso

Essas instruções mostram como mudar manualmente a senha para a palavra -
"secret"

1.  No phpMyAdmin selecione o banco de dados do site Joomla! na listagem
    do lado esquerdo, para ver as tabelas do banco.

2.  Encontre e clique sobre a tabela com o sufixo "\_users" (Obs.: o
    prefixo pode não ser jos\_).

3.  Clique no botão "Browse" no topo. Isso exibirá todos os usuários
    cadastrados no site.

4.  Encontre o usuário que quer mudar a senha. Pressione o ícone Editar
    da linha.

5.  O formulário apresentado permitirá que se edite o campo da senha.
    Copie o valor

        d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199

    para o campo e clique no botão *Go*. O phpMyAdmin deverá exibir uma
    mensagem "Affected rows: 1". A senha foi modificada para
    **"secret"**.

6.  Acesse com o usuário e a senha acima e mude-os imediatamente após
    login. Verifique que todos os usuários no Gerenciador estão
    corretos. Se você foi hackeado, você poderá mudar todas as senhas do
    site.

### Crie um novo Super Usuário

Se mudar a senha não funcionar ou você não tem certeza qual usuário faz
parte do grupo Super Users, com esse método é possível criar um novo
usuário.

1.  No phpMyAdmin selecione o banco de dados do site Joomla! na listagem
    do lado esquerdo, para ver as tabelas do banco.
2.  Clique no botão "SQL" na barra de ferramentas para rodar uma query
    SQL no banco de dados selecionado. Isso exibirá um campo chamado
    "Run SQL query/queries on database ".
3.  Apague qualquer texto que apareça nesse campo, copie e cole a query
    abaixo e aperte o botão *Go* para continuar e criar o novo usuário
    administrador à tabela.
4.  Use a query SQL query abaixo para criar outra conta de
    administrador.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Certifique-se que o prefixo coincide
com o do seu banco!

O código a seguir usa o prefixo de tabela jos31\_ como exemplo. Quando
se instalou o Joomla! pela primeira vez o prefixo é **ALEATÓRIO** ou
outro que se tenha definido. Será necessário mudar todas as ocorrências
de **jos31\_** no código abaixo para aquela usada na sua instalação.

**Código SQL para uso com Joomla
 <img src="https://docs.joomla.org/images/5/53/Compat_icon_2_5.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 2.5" /> <img src="https://docs.joomla.org/images/4/4d/Compat_icon_3_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 3.x" /> <img src="https://docs.joomla.org/images/b/bd/Compat_icon_4_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 4.x" />**

    INSERT INTO `jos31_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `jos31_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');

Agora será possível acessar o Painel de Administração do Joomla! com o
nome de usuário "admin2" e a senha "secret". Depois de entrar, vá ao
Gerenciador de Usuários, mude a senha e adicione um e-mail válido à
conta. Caso seu site tenha sido hackeado, certifique-se que todo os
usuários estão corretos, especialmente aqueles do grupo Super Users.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Warning!

Cuidado: as senhas apresentadas aqui são de conhecimento público para
recuperação apenas. Seu site poderá ser hackeado se não mudá-las depois
de acessar. Certifique-se de fazer essa mudança.


Os exemplos acima mudam a senha para "secret". Outros dois valores
possíveis são mostrados abaixo:

    - password = "this is the MD5 and salted hashed password"
    ------------------------------------------------------
    - admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
    - secret = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
    - OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm
