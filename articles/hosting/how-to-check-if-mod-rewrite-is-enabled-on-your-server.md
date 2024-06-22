<!-- Filename: How_to_check_if_mod_rewrite_is_enabled_on_your_server / Display title: Como verificar se o mod de reescrita está habilitado no seu servidor -->

Muitos problemas com a SEO surgem do fato de que um host não ativou o
mod_rewrite (configuração do Apache) nos servidores. Eles costumam dizer
que o fizeram (quando na verdade não o fizeram). Você pode verificar se
isso está correto ou não e se isso está fazendo com que seu servidor
emita o erro HTTP 500.

Aqui está como verificar se o mod_rewrite está realmente ativado!

**1. Ative a SEO em sua administração**:

Site -\> Configurações globais -\> Configurações de SEO: URLs amigáveis
para mecanismos de pesquisas para Sim, usar a reescrita do URL para Sim.
(Configurar a adição de sufixo aos URLs é opcional).

  
**2. Renomeie seu htaccess.txt para .htaccess**:

Em seguida coloque apenas as seguintes linhas em seu .htaccess:

    RewriteEngine On
    Options +FollowSymLinks
    RewriteRule ^joomla\.html http://www.joomla.org/? [R=303,L]

  
**3. Agora aponte seu navegador para**
<a href="http://www.example.com/joomla.html" class="external free"
target="_blank"
rel="nofollow noreferrer noopener">http://www.example.com/joomla.html</a>

(Substitua www.example.com pelo seu próprio nome de domínio no URL
acima.)

Se ele redirecionar você para joomla.org, o mod_rewrite está
funcionando. Se resultar em um erro, o mod_rewrite não está funcionando.

Nota: se o seu site estiver localizado em uma pasta como "/test/" você
precisa inserir o código no arquivo .htaccess da raiz da seguinte forma:

    RewriteEngine On
    Options +FollowSymLinks
    RewriteRule ^test/joomla\.html http://www.joomla.org/? [R=303,L]
