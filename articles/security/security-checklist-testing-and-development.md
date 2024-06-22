<!-- Filename: Security_Checklist/Testing_and_Development / Display title: Lista de verificação de segurança/Testes e desenvolvimento -->

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

## Testes e desenvolvimento seguros

### Desenvolva localmente, implante globalmente

Desenvolva e teste seu site em uma máquina local primeiro. Instalar o
Joomla localmente não é tão difícil quanto pode parecer e o exercício
aumentará muito sua confiança.

### Use um ambiente de desenvolvimento integrado

Considere usar um ambiente de desenvolvimento integrado (IDE). Um IDE
gratuito que muitos desenvolvedores do Joomla! usam é o
<a href="https://code.visualstudio.com/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">Visual Studio
Code</a>. Consulte também [Configurando o Visual Studio Code para
desenvolvimento do
joomla](https://docs.joomla.org/Visual_Studio_Code "Special:MyLanguage/Visual Studio Code")
para obter instruções sobre como instalar e configurar o Visual Studio
Code.

### Use um sistema de versionamento

Seja capaz de reverter para uma versão anterior do seu site usando um
sistema de controle de versão moderno, normalmente
<a href="https://git-scm.com/" class="external text" target="_blank"
rel="nofollow noreferrer noopener">git</a>. O IDE do Visual Studio Code
indicado acima inclui plugins para git. Isso permite que você trabalhe
com o repositório de origem do Joomla! hospedado no
<a href="https://github.com/joomla/joomla-cms/releases"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">GitHub</a>, bem como quaisquer outros
projetos no GitHub, no GitLab ou no BitBucket (os 3 sistemas de
versionamento git mais populares).

### Mais ferramentas sugeridas

Confira a lista de
<a href="http://forum.joomla.org/index.php/topic,25307.0.html"
class="external text" target="_blank"
rel="noreferrer noopener">Softwares e ferramentas populares para
desenvolvedores</a> da comunidade do Joomla!.

## Configure um processo de cópia de segurança primeiro

### A regra mais importante

**Você sempre será capaz de retornar seu site a um estado de
funcionamento anterior por meio do uso regular de um processo de cópia
de segurança e recuperação externo forte.**

Certifique-se de que seu processo de cópia de segurança e recuperação
esteja pronto e testado antes de seu site entrar no ar.

Esta é a melhor maneira (e muitas vezes a única) de se recuperar de
catástrofes inevitáveis como:

1.  Um site comprometido/craqueado.
2.  Site quebrado devido a uma atualização defeituosa.
3.  Falha de hardware, como discos rígidos inoperantes, falhas de
    energia, roubo de servidor, etc.
4.  Intervenção autoritária do governo. (Mais comum do que alguns
    imaginam.)
5.  Necessidade de se mudar rapidamente para um novo servidor ou
    provedor de hospedagem.
