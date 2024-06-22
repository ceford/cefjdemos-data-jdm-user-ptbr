<!-- Filename: Enabling_HTTPS_on_your_site / Display title: Habilitando o https em seu site -->

<table class="navbox" data-cellspacing="0">

<tbody>
<tr class="odd">
<td><table class="nowraplinks navbox-inner" data-cellspacing="0">

<tbody>
<tr class="header">
<th colspan="2" class="navbox-title" scope="col">Security Checklist <img
src="https://docs.joomla.org/images/7/7b/Compat_icon_CMS.png"
decoding="async" data-file-width="87" data-file-height="17" width="87"
height="17" alt="Joomla CMS" /></th>
</tr>
&#10;<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-abovebelow"></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-list navbox-odd"><table
class="nowraplinks navbox-subgroup" data-cellspacing="0">

<tbody>
<tr class="header">
<th colspan="2" class="navbox-title" scope="col"><em>Articles in this
series</em></th>
</tr>
&#10;<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-list navbox-odd"><ul>
<li><a href="https://docs.joomla.org/Security_Checklist/Getting_Started"
title="Special:MyLanguage/Security Checklist/Getting Started">Primeiros
passos</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Hosting_and_Server_Setup"
title="Special:MyLanguage/Security Checklist/Hosting and Server Setup">Hospedagem
e configuração de servidor</a></li>
<li><a href="https://docs.joomla.org/Enabling_HTTPS_on_your_site"
title="Special:MyLanguage/Enabling HTTPS on your site">Habilitando o
HTTPS em seu site</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Where_can_you_learn_more_about_file_permissions%3F"
title="Special:MyLanguage/Security Checklist/Where can you learn more about file permissions?">Saiba
mais sobre permissões de arquivo</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Testing_and_Development"
title="Special:MyLanguage/Security Checklist/Testing and Development">Testes
e desenvolvimento</a></li>
<li><a href="https://docs.joomla.org/Security_Checklist/Joomla!_Setup"
title="Special:MyLanguage/Security Checklist/Joomla! Setup">Configuração
do Joomla!</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Administration">Administração
do site</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Recovery">Recuperação
de sites</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/You_have_been_hacked_or_defaced"
title="Special:MyLanguage/Security Checklist/You have been hacked or defaced">Você
foi hackeado ou adulterado</a></li>
</ul></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

## O que é ssl/tls?

A segurança da camada da transporte (do inglês transport layer
security - tls) é a sucessora da camada de soquetes segura (do inglês
secure sockets layer - ssl) - embora a maioria das pessoas ainda se
refira a ela como ssl nas postagens de blogs. Já notou o sinal de
cadeado ao lado da url quando você navega na Internet? Isso significa
que todos os dados que você envia para esse site estão sendo enviados
criptografados para que qualquer pessoa que possa ter invadido sua rede
(ou similar) e possa interceptar suas solicitações não consiga
visualizar nenhum dos dados - elas só podem ver quais urls você está
acessando .

## Por que usar a tls?

O Google (e a maioria dos outros mecanismos de pesquisa) agora tratam os
sites que usam o https com preferência<sup>[\[1\]](#cite_note-1)</sup>.
Além disso, muitos navegadores sinalizam qualquer site com um formulário
(como um formulário de início de sessão ou contato) que não esteja
usando o https<sup>[\[2\]](#cite_note-2)</sup>

## Como faço para configurar a tls?

Para configurar o certificado, a maneira mais simples é fazer com que
seu host faça isso por você.

O certificado correto para comprar depende das proteções de segurança
exigidas em seu site. Se você não sabe, provavelmente a opção mais
barata e fácil é usar a
<a href="https://letsencrypt.org/" class="external text" target="_blank"
rel="nofollow noreferrer noopener">Let's Encrypt</a> - é gratuito e,
dependendo do seu host, pode ser configurado diretamente do seu painel
de hospedagem cpanel ou plesk.

Se você comprou um endereço de protocolo de Internet (Ip) dedicado e o
certificado da ssl, simplesmente peça ajuda ao seu host e eles o
assinarão e o instalarão no local correto para você.

## Como redireciono todo o meu tráfego para o https

### No Joomla

A maneira mais fácil de impor o tráfego em https é fazê-lo no Joomla. Em
"configuração global" existe a opção "forçar https" que permite forçar o
uso do https apenas na área do administrador ou em todo o site. Você
quase sempre vai querer a última.

<img
src="https://docs.joomla.org/images/thumb/6/6d/Enable_HTTPS_In_Global_Config-en.png/800px-Enable_HTTPS_In_Global_Config-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/6/6d/Enable_HTTPS_In_Global_Config-en.png/1200px-Enable_HTTPS_In_Global_Config-en.png 1.5x, https://docs.joomla.org/images/6/6d/Enable_HTTPS_In_Global_Config-en.png 2x"
data-file-width="1512" data-file-height="1012" width="800" height="535"
alt="Image Showing the Force HTTPS option in the Joomla 3.x default backend template" />

### No .htaccess

    RewriteEngine on
    RewriteCond %{SERVER_PORT} !^443$
    RewriteRule .* https://%{HTTP_HOST}%{REQUEST_URI} [QSA,R=301,L]

    Redirect permanent / https://www.yourdomainname.com

#### Exemplos de .htaccess mais complexos

Como exemplo, para alternar do http para o https em qualquer página que
tenha "abc/def" ou "ghi" na url, adicione algo assim:

Código:

    RewriteCond %{HTTPS} off
    RewriteRule ^(abc/def|ghi)(.*)/?$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,NC,L]

... e para mudar de https de volta para http em qualquer página que
tenha "home" ou "help" na url, faça algo assim:

Código:

    RewriteCond %{HTTPS} on
    RewriteRule ^(home|help)(.*)/?$ http://%{HTTP_HOST}%{REQUEST_URI} [R=301,NC,L]

Se você deseja forçar o uso da ssl em uma pasta específica, você pode
inserir o código abaixo em um arquivo .htaccess colocado nessa pasta
específica:

Código:

    RewriteEngine On 
    RewriteCond %{REQUEST_URI} folder 
    RewriteRule ^(.*)$ https://www.example.com/folder/$1 [R,L]

Certifique-se de alterar a referência da pasta para o nome real da
pasta. Em seguida, certifique-se de substituir www.example.com/folder
pelo nome de domínio real e pela pasta na qual deseja forçar a
utilização da ssl.

1.  <span id="cite_note-1">[↑](#cite_ref-1) <a
    href="https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html"
    class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html</a></span>
2.  <span id="cite_note-2">[↑](#cite_ref-2) <a
    href="https://www.blog.google/products/chrome/milestone-chrome-security-marking-http-not-secure/"
    class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://www.blog.google/products/chrome/milestone-chrome-security-marking-http-not-secure/</a></span>
