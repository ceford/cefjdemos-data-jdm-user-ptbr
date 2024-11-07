<!-- Filename: J4.x:Assorted_Issues / Display title: Questões Diversas -->

## Problema de Redirecionamento Após Atualização para 4.0.6

Isso é um bug! Linha 243 de *plugins/system/redirect/redirect.php*:

       $db->updateObject('#__redirect_links', $redirect, 'id');

deveria ser

       $this->db->updateObject('#__redirect_links', $redirect, 'id');

## Uma Página Exibe Sem Estilização

Possível causa: Uma seção gzip no arquivo *.htaccess* está comprimindo os arquivos CSS e JavaScript que já estão comprimidos.

Veja esta seção do arquivo *.htaccess*:

    ## Essas diretivas são habilitadas apenas se o módulo mod_headers do Apache estiver ativado.
    ## Esta seção verificará se existe um arquivo .gz e, se existir, o transmitirá
    ##     diretamente ou fará a compressão gzip de qualquer recurso rapidamente
    ## Se seu site começar a aparecer estranho após habilitar isso, e você ver
    ##     ERR_CONTENT_DECODING_FAILED na aba de rede do console do seu navegador,
    ##     então seu servidor já está fazendo a compressão gzip dos arquivos css e js e você não precisa
    ##     desse bloco habilitado no seu .htaccess

    ...

Se presente, comente ou remova.

## A Lista de Módulos do Site Está Vazia

Possível causa: O tamanho do buffer de ordenação do MySQL pode ser muito pequeno.

Usando o phpMyAdmin, vá para **Início**→**Variáveis**→**Tamanho do buffer de ordenação**.

Ele deve ser pelo menos 256K, preferencialmente 512K. Em alguns serviços de hospedagem compartilhada, pode estar configurado para 128K. Peça ao serviço de hospedagem para aumentá-lo.  

## Atualização Falha após Atualizar para 4.0.4

Causa: uma alteração essencial no procedimento de atualização que afeta um pequeno
número de usuários.

Procure por esta linha em *.htaccess*:

```plaintext
RewriteRule ^administrator/components/com_joomlaupdate/restore\.php$ - [L]
```

Altere para:

```plaintext
RewriteRule ^administrator\/components\/com_joomlaupdate\/extract\.php$ - [L]
```

Para mais informações, veja:

<a
href="https://www.joomla.org/announcements/release-news/5850-changes-to-update-process-that-you-need-to-be-aware-of.html"
rel="noreferrer noopener">Alterações
no Processo de Atualização que você precisa estar ciente</a>

## Artigos Visíveis no Banco de Dados e Frontend, mas Não Visíveis no Backend

Isso ocorre quando artigos são importados diretamente no banco de dados, o que funcionava bem no Joomla 3, mas não no Joomla 4. A solução de um usuário é a seguinte:

    Eu importei artigos diretamente no banco de dados na tabela #__content, como sempre fazia no Joomla 3.
    Porém, no Joomla 4, eles não estavam visíveis.

    Em Conteúdo > Categorias, os contadores de itens da categoria contavam os artigos importados.
    Mas eles não estavam visíveis em Conteúdo > Artigos.

    Resolvi isso criando as referências necessárias na tabela #__workflow_associations para cada artigo importado:
    item_id = ID do artigo, stage_id = 1 e extensão = com_content.article.

Com isso de outro usuário:

Essa consulta deve resolver o problema para você. Substitua \#\_\_ pelo seu próprio prefixo de banco de dados.

Esta consulta evita itens duplicados na tabela de associações de workflow:

    INSERT INTO #__workflow_associations (item_id, stage_id, extension) 
    SELECT c.id as item_id, '1', 'com_content.article' FROM #__content AS c 
    WHERE NOT EXISTS (SELECT wa.item_id FROM #__workflow_associations AS wa WHERE wa.item_id = c.id);

*Traduzido por openai.com*

