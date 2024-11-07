<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Nginx / Display title: URLs Amigáveis no Nginx -->

## Introdução

URLs amigáveis para mecanismos de busca (SEF), legíveis para humanos ou URLs limpas são URLs que fazem sentido tanto para humanos quanto para mecanismos de busca, pois explicam o caminho até a página específica a que apontam. O Joomla! é capaz de criar e analisar URLs em qualquer formato, incluindo URLs SEF. Isso não depende da reescrita de URL executada pelo servidor web, por isso funciona mesmo se o Joomla! estiver em execução em um servidor que não seja o Apache com o módulo mod_rewrite. As URLs SEF seguem um certo padrão fixo, mas o usuário pode definir um texto descritivo curto (alias) para cada segmento da URL.

Internamente, a parte local de uma URL SEF (a parte após o nome de domínio) é chamada de rota. Criar e processar URLs SEF é, portanto, referido como roteamento, e o código relevante é chamado de roteador.

Este artigo aborda URLs SEF no popular servidor web open-source Nginx.

## Passos para Servidores NginX¶

- Adicione o seguinte código à configuração do seu servidor (vhost) no arquivo nginx.conf:

```
    # Suporte a URLs Limpas (também conhecidas como URLs Amigáveis para Motores de Busca)
    location / {
       try_files $uri $uri/ /index.php?$args;
    }
```
- Se o código acima não funcionar, adicione o seguinte código à configuração do seu servidor no arquivo nginx.conf: (Isso funcionou com nginx 1.4.6 no Ubuntu.)
```
    server {
      ....
      location / {
      expires 1d;

      # Habilitar URLs SEF do Joomla dentro do Nginx
      try_files $uri $uri/ /index.php?$args;
      }
      ....
    }
```
- Faça login no seu Backend e abra a Configuração Global
- Habilite a opção **URLs Amigáveis para Motores de Busca** e salve. Esta opção converte os URLs do formato nativo do Joomla! para o formato SEF. Verifique se o seu site funciona corretamente. Seus URLs agora devem parecer com `http://www.example.com/index.php/the-­news/1­-latest­-news/1­-welcome­-to­-joomla`. Se o seu site não funcionar corretamente, veja [Por que seu site fica bagunçado quando você ativa URLs Amigáveis para Motores de Busca (SEF)?](https://docs.joomla.org/Why_does_your_site_get_messed_up_when_you_turn_on_SEF_(Search_Engine_Friendly_URLs)%3F)
- Habilite a opção **Usar reescrita de URL/mod_rewrite do Apache** e salve. Esta opção usa a função mod_rewrite do Apache para eliminar a parte *index.php* da URL Verifique se o seu site funciona corretamente. Seus URLs agora devem parecer com `http://www.example.com/the-news/1-latest-news/1-welcome-to-joomla`. Se esta opção causar erros, veja [Como verificar se o mod_rewrite está habilitado no seu servidor](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server). Se não estiver habilitado e você tiver acesso ao arquivo `apache/conf/httpd.conf`, abra esse arquivo e verifique se a linha `LoadModule rewrite_module modules/mod_rewrite.so` está descomentada. Se necessário, descomente a linha e reinicie o servidor web Apache. Se o *mod_rewrite* não puder ser habilitado, deixe essa opção desativada. Não importa se você deixar o arquivo `.htaccess` renomeado.
- *Se você considerar necessário*, habilite **Adicionar sufixo às URLs** e *salve*. Esta opção adiciona `.html` ao final das URLs. Existem diferentes opiniões sobre se isso é necessário ou mesmo útil. Os motores de busca não parecem se importar se os seus URLs terminam em `.html` ou não.
- Abra o Gerenciador de Plugins e habilite o plugin **Sistema - SEF**. Este plugin adiciona suporte SEF aos links em seus artigos do Joomla. Ele opera diretamente no HTML e não requer uma tag especial.

*Traduzido por openai.com*

