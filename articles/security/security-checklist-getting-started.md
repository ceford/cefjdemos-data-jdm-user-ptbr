<!-- Filename: Security_Checklist/Getting_Started / Display title: Lista de verificação de segurança/Primeiros passos -->

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
title="Special:MyLanguage/Security Checklist/Getting Started">Getting
Started</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Hosting_and_Server_Setup"
title="Special:MyLanguage/Security Checklist/Hosting and Server Setup">Hosting
and Server Setup</a></li>
<li><a href="https://docs.joomla.org/Enabling_HTTPS_on_your_site"
title="Special:MyLanguage/Enabling HTTPS on your site">Enabling HTTPS on
your site</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Where_can_you_learn_more_about_file_permissions%3F"
title="Special:MyLanguage/Security Checklist/Where can you learn more about file permissions?">Learn
about file permissions</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Testing_and_Development"
title="Special:MyLanguage/Security Checklist/Testing and Development">Testing
and Development</a></li>
<li><a href="https://docs.joomla.org/Security_Checklist/Joomla!_Setup"
title="Special:MyLanguage/Security Checklist/Joomla! Setup">Joomla!
Setup</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Administration">Site
Administration</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Recovery">Site
Recovery</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/You_have_been_hacked_or_defaced"
title="Special:MyLanguage/Security Checklist/You have been hacked or defaced">You
have been hacked or defaced</a></li>
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

### Segurança importa

A segurança na Internet é um desafio em rápida evolução e uma ameaça
sempre presente. Não existe uma maneira certa de proteger um site, e
todos os métodos de segurança estão sujeitos a obsolescência
instantânea, melhoria incremental e revisão constante. Todos os sites
voltados para o público estão abertos a ataques constantes. Você está
disposto e apto a investir o tempo necessário para administrar um site
dinâmico, 24 horas por dia, 7 dias por semana, acessível por todo o
mundo, orientado a banco de dados, interativo e autenticado pelo
usuário? Você tem tempo e recursos para responder ao fluxo constante de
novos problemas de segurança na Internet? Os [10 truques de
administrador mais
estúpidos](https://docs.joomla.org/Top_10_Stupidest_Administrator_Tricks "Top 10 Stupidest Administrator Tricks")
é uma visão cômica/trágica do que pode dar errado. Não aprenda esses
truques da maneira mais difícil! Dependendo de sua própria experiência,
ler os *truques mais estúpidos* fará você rir ou chorar. Felizmente,
existem alguns princípios bem estabelecidos sobre os quais basear seus
planos defensivos. As listas de verificação a seguir apontam para as
práticas recomendadas atuais para a segurança do Joomla.

### Como ler esses documentos

1.  Nem todas as técnicas são apropriadas para todos os níveis de
    experiência. Aplique as técnicas que você entende e leia as que você
    não entende.
2.  Nem todas as técnicas são apropriadas para todos os servidores. Se
    você usa um servidor compartilhado, deve depender das configurações
    estabelecidas pelo seu provedor de hospedagem. Se você estiver
    usando um servidor virtual ou dedicado, poderá aplicar táticas de
    segurança mais criativas.
3.  Nem todas as táticas de segurança são apropriadas para todas as
    versões do Joomla. Quando uma técnica se aplica a apenas uma versão,
    ela é indicada por um dos seguintes ícones:
     <img src="https://docs.joomla.org/images/4/43/Compat_icon_1_0.png"
    decoding="async" data-file-width="40" data-file-height="17" width="40"
    height="17" alt="Joomla 1.0" /> <img src="https://docs.joomla.org/images/c/c8/Compat_icon_1_5.png"
    decoding="async" data-file-width="40" data-file-height="17" width="40"
    height="17" alt="Joomla 1.5" /> <img src="https://docs.joomla.org/images/d/da/Compat_icon_1_6.png"
    decoding="async" data-file-width="40" data-file-height="17" width="40"
    height="17" alt="Joomla 1.6" /> <img src="https://docs.joomla.org/images/8/87/Compat_icon_1_7.png"
    decoding="async" data-file-width="40" data-file-height="17" width="40"
    height="17" alt="Joomla 1.7" /> <img src="https://docs.joomla.org/images/5/53/Compat_icon_2_5.png"
    decoding="async" data-file-width="40" data-file-height="17" width="40"
    height="17" alt="Joomla 2.5" /> <img src="https://docs.joomla.org/images/9/9e/Compat_icon_3_0.png"
    decoding="async" data-file-width="40" data-file-height="17" width="40"
    height="17" alt="Joomla 3.0" /> <img src="https://docs.joomla.org/images/d/d6/Compat_icon_3_1.png"
    decoding="async" data-file-width="40" data-file-height="17" width="40"
    height="17" alt="Joomla 3.1" />

### As orientações mais importantes

Essas listas de verificação são longas e crescentes porque o enredo
completo é denso, complexo e em expansão, mas não se desespere! Aqui
estão algumas diretrizes essenciais para proteger qualquer site.
Segui-los irá protegê-lo da maioria das catástrofes.

1.  **Faça cópia de segurança cedo e com frequência:** Configure (e use
    e teste) um processo regular de cópia de segurança e recuperação.
    Quando bem feito, isso garante que você possa se recuperar de quase
    qualquer desastre imaginável.
2.  **Atualize cedo e frequentemente:** Atualize imediatamente para a
    última versão *estável* do Joomla! e quaisquer extensões de
    terceiros instaladas. Isso garante que seu site esteja protegido das
    vulnerabilidades mais recentes assim que uma correção for lançada e
    dos métodos de ataque mais recentes assim que uma defesa for
    desenvolvida.
3.  **Use um host seguro**: Use um host da web de alta qualidade. Não se
    deixe enganar por ofertas de "largura de banda ilimitada, espaço
    ilimitado em disco rígido, bancos de dados ilimitados, etc.
4.  **Use a comunidade**: Não se esqueça do truísmo, "Se um negócio é
    bom demais para ser verdade, é." Parece que nada na Terra é
    ilimitado – exceto talvez a credulidade dos tolos e a ganância
    daqueles que os atacam. Considere contratar assistência profissional
    se você tiver experiência ou conhecimento inadequados nessa área.
    Uma das vantagens do software GNU é que o suporte ao usuário é
    gratuito. Tire proveito disso fazendo boas perguntas nos
    <a href="http://forum.joomla.org" class="external text" target="_blank"
    rel="noreferrer noopener">Fóruns do Joomla!</a>. Ao fazer isso,
    certifique-se de usar o quadro mais adequado, como Instalação,
    Migração e atualização, Administração.

As postagens mais úteis no Fórum de segurança do Joomla! são convertidas
em  Perguntas frequentes de segurança e
desempenho.
Muitos dos itens desta lista são explicados com muito mais detalhes nas
Perguntas frequentes.

Você pode querer ler o excelente  Guia absoluto para iniciantes no
Joomla!
Ele tem muitas dicas e truques apresentada(o)s em um formato fácil de
entender. Mesmo entusiastas experientes no Joomla encontram ótimas
ideias aqui.

Cace as muitas pepitas de sabedoria encontradas nos
<a href="http://forum.joomla.org" class="external text" target="_blank"
rel="noreferrer noopener">Fóruns do Joomla!</a>, em particular no
<a href="http://forum.joomla.org/viewforum.php?f=714"
class="external text" target="_blank" rel="noreferrer noopener">Fórum de
segurança do Joomla! 3.x</a> e no
<a href="http://forum.joomla.org/viewforum.php?f=621"
class="external text" target="_blank" rel="noreferrer noopener">Fórum de
segurança do Joomla! 2.x</a>.

Para receber todos os anúncios de segurança do Joomla, assine as
Notícias de segurança do Joomla. Existem várias formas de subscrever:

1.  <a
    href="http://feedburner.google.com/fb/a/mailverify?uri=JoomlaSecurityNews"
    class="external text" target="_blank"
    rel="nofollow noreferrer noopener">Notificação automática por e-mail</a>
2.  <a href="http://feeds.joomla.org/JoomlaSecurityNews"
    class="external text" target="_blank" rel="noreferrer noopener">Feed
    RSS</a>.

### As más notícias

1.  **Não existe segurança perfeita na web!** Como diriam os
    economistas, "Não existe almoço grátis." Não se deixe enganar pela
    premiada facilidade de uso do Joomla. Manter um site seguro na
    Internet aberta não é fácil. Manter a segurança adequada requer uma
    ampla e crescente gama de habilidades e conhecimentos, vigilância
    constante e um processo robusto de cópia de segurança e recuperação.
2.  **Não existe um caminho certo!** Devido à variedade e complexidade
    dos sistemas web modernos, os problemas de segurança não podem ser
    resolvidos com soluções simples e de tamanho único. Você (ou alguém
    de sua confiança) deve aprender o suficiente sobre sua
    infraestrutura de servidor para tomar decisões de segurança válidas.
    A segurança forte é um alvo em movimento. O especialista de hoje
    pode ser a vítima de amanhã. Bem vindo ao jogo...
3.  **Não há substituto para a experiência!** Para proteger seu site,
    você deve ganhar experiência real (algumas das quais serão amargas)
    ou obter ajuda experiente de outras pessoas. Se você não investiu o
    tempo considerável que leva para aprender a manter um site seguro,
    certifique-se de consultar alguém que o tenha feito. Leia esta
    descrição irônica dos  10 truques de administrador mais
    estúpidos,
    que ilustra exemplos típicos, passo a passo, de como aprender
    segurança na web da maneira mais difícil.

### As boas notícias

1.  **Mesmo um iniciante pode começar na cabeça do rebanho** Fóruns de
    usuários para muitos sistemas estão entupidos com postagens do tipo
    <a href="http://www.google.com/search?q=Ajuda!+Fui+hackeado"
    class="external text" target="_blank"
    rel="nofollow noreferrer noopener">Ajuda! Fui hackeado</a> de
    pessoas que não seguiram as práticas de segurança padrão. Se você
    está estudando esta lista de verificação antes de seu site ser
    atacado, parabéns, você já está à frente do rebanho.
2.  **Não é tão difícil quanto parece** Se este é um dos seus primeiros
    sites, os problemas de segurança podem parecer esmagadores, mas você
    não precisa lidar com todos eles de uma vez. Comece com os problemas
    mais críticos. À medida que você se familiariza com as ferramentas e
    técnicas
    <a href="http://www.gnu.org" class="external text" target="_blank"
    rel="nofollow noreferrer noopener">GNU</a>, incluindo
    <a href="http://www.gnu.org/" class="external text" target="_blank"
    rel="nofollow noreferrer noopener">GNU/Linux</a>,
    <a href="http://www.apache.org" class="external text" target="_blank"
    rel="nofollow noreferrer noopener">Apache</a>,
    <a href="http://www.mysql.com" class="external text" target="_blank"
    rel="nofollow noreferrer noopener">MySQL</a>,
    <a href="http://en.wikipedia.org/wiki/SQL" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">SQL</a>,
    <a href="http://www.php.net" class="external text" target="_blank"
    rel="nofollow noreferrer noopener">PHP</a>,
    <a href="http://en.wikipedia.org/wiki/HTTP" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">HTTP</a>,
    <a href="http://en.wikipedia.org/wiki/CSS" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">CSS</a>,
    <a href="http://en.wikipedia.org/wiki/XML" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">XML</a>,
    <a href="http://en.wikipedia.org/wiki/RSS" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">RSS</a>,
    <a href="http://en.wikipedia.org/wiki/TCP/IP" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">TCP/IP</a>,
    <a href="http://en.wikipedia.org/wiki/FTP" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">FTP</a>,
    <a href="https://git-scm.com/" class="external text" target="_blank"
    rel="nofollow noreferrer noopener">Git</a>,
    <a href="http://en.wikipedia.org/wiki/JavaScript" class="external text"
    target="_blank" rel="nofollow noreferrer noopener">JavaScript</a>, e
    o
    <a href="http://www.joomla.org" class="external text" target="_blank"
    rel="noreferrer noopener">Joomla!</a>, você adicionará refinamentos
    ao seu conjunto de táticas de segurança.
3.  **Você pode obter ajuda** Se você acredita que seu site foi atacado,
    **não** poste simplesmente um anúncio com detalhes completos nos
    fóruns do Joomla!. Se você estiver lidando com uma nova
    vulnerabilidade ou nova forma de ataque, publicar essas informações
    pode colocar outros sites em risco. Em vez disso, relate possíveis
    vulnerabilidades de segurança à
    <a href="http://developer.joomla.org/security" class="external text"
    target="_blank" rel="noreferrer noopener">Força-tarefa de segurança do
    Joomla!</a>.
