<!-- Filename: How_do_you_block_direct_hot_linking_to_image_files_using_htaccess%3F / Display title: Desativar Hotlinking de Imagens -->

## Definição

Hotlinking é a prática de vincular uma imagem em um site a partir de um artigo em outro site. Pode ser uma prática muito útil. Este site utiliza muitas imagens que estão, na verdade, localizadas no site docs.joomla.org. Isso economiza o tempo e o esforço necessários para criar capturas de tela e na largura de banda deste site. No entanto, podem haver questões de direitos autorais e você pode querer evitar que suas imagens sejam usadas dessa forma.

O método descrito aqui utiliza um arquivo *.htaccess*, que é uma funcionalidade do servidor Apache. Outros servidores web podem oferecer outros métodos para prevenir o hotlinking.  

## Instruções

Coloque o seguinte código no arquivo *.htaccess* do seu diretório raiz.

```
<IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteCond %{HTTP_REFERER} !^$
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?seudominio.com [NC]
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?google.com [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```

### Explicação

* A primeira RewriteCond permite solicitações diretas usando uma URL - sem referenciador.
* A segunda RewriteCond permite solicitações do seu próprio domínio. A flag *\[NC\]*
    significa *No Case*, ou seja, corresponde tanto a caracteres maiúsculos quanto minúsculos.
* A terceira RewriteCond permite solicitações do Google, para que suas imagens
    ainda possam aparecer nos resultados de pesquisa. Você pode adicionar linhas semelhantes para
    quaisquer outros sites que você deseje permitir.
* A RewriteRule bloqueia solicitações de arquivos de imagem de todos os domínios
    não previamente permitidos. A flag F informa ao navegador para retornar um cabeçalho
    Proibido (403). L significa Última regra.

### Bloquear Hot Linking de Domínios Específicos

Para interromper o hotlinking de domínios específicos apenas, como *myspace.com*,
*blogspot.com* e *livejournal.com*, enquanto permite que outros sites
façam hotlink para suas imagens, use o código a seguir:

```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?myspace\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?blogspot\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?livejournal\.com/ [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```

Você pode adicionar quantos domínios diferentes quiser. Cada linha de *RewriteCond*,
exceto a última, deve terminar com as flags *\[NC,OR\]*. *NC*
significa ignorar case. *OR* significa "Ou Próximo", ou seja, corresponder a esta linha
**ou** a próxima linha. A última *RewriteCond* omite a flag *OR* para parar
a correspondência após a última *RewriteCond*.

*Traduzido por openai.com*

