<!-- Filename: How_do_Windows_file_permissions_work%3F / Display title: Como funcionam as permissões de arquivo do Windows? -->

<img
src="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/25px-Copyedit.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/38px-Copyedit.png 1.5x, https://docs.joomla.org/images/thumb/4/47/Copyedit.png/50px-Copyedit.png 2x"
data-file-width="200" data-file-height="200" width="25" height="25"
alt="Copyedit.png" />This Article Needs Your Help

*This article is tagged because it* **NEEDS REVIEW***. You can help the
Joomla! Documentation Wiki by <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=How_do_Windows_file_permissions_work%3F/pt-br&amp;action=edit"
class="external text" target="_blank"
rel="noreferrer noopener">contributing to it</a>.
<span class="small">More pages that need help similar to this one are
here.</span>
<span class="small">**NOTE-If you feel the need is satistified, please
remove this notice.**</span>*
**Reason:** A better title is probably in order too. Something like
**Windows Server Permissions for Joomla! Installations** or something
similar and less wordy.

## O Joomla e as permissões de arquivo do Windows - Explicação

Para aqueles que estão desenvolvendo ou entregando seus websites Joomla!
de um ambiente Windows, às vezes é difícil obter informações relevantes
sobre permissões. Infelizmente, é um fato que a maioria dos serviços da
web são oferecidos no Unix e que o Unix está muito bem documentado nesse
ambiente. Espero que as informações a seguir ajudem de alguma forma a
esclarecer qualquer confusão e fornecer um pouco de orientação também.

##### Visão geral dos servidores web do Windows

Em primeiro lugar, vamos discutir as diferenças entre os servidores. Em
geral, a maioria das pessoas do Windows parece estar usando o Apache
(Win32) ou o IIS da Microsoft, esses dois servidores web operam de
maneira muito diferente e utilizam modelos de entrega ligeiramente
diferentes. O Apache (Win32) geralmente é executado no computador host
como o usuário em que foi instalado, enquanto o IIS é instalado em um
usuário específico mas será executado em um usuário "IUSR\_"
recém-instalado.

##### Padrões de permissão

Por padrão, o Unix tende a apenas dar acesso total aos arquivos e
diretórios ao usuário "proprietário" e o Windows, em oposição a essa
abordagem, por padrão também atribuirá permissões completas ao grupo
"Todos". A primeira coisa que qualquer bom administrador do Windows fará
é remover os direitos do grupo "Todos" para melhorar a segurança. Isso
provavelmente não é necessário para testes locais mas explica por que se
"Todos" não for removido e você executar algum tipo de script de
verificação de permissões ou a verificação de pré-instalação do Joomla!,
no geral, você terá permissões completas de "ler, gravar e executar",
porque você está adquirindo os direitos do grupo "Todos".

##### Servidor de informações de Internet da Microsoft (IIS)

O IIS vem em dois tipos principais, o PWS (Servidor web pessoal) e o IIS
(servidor de informações de Internet). Essencialmente, estes são a mesma
aplicação. O PWS é apenas uma versão reduzida do IIS projetada para
ambientes de desktop, enquanto o IIS é projetado para ambientes de
servidor. O PWS limita você a um único site principal, portanto, as
instalações de seus aplicativos geralmente estarão em subdiretórios do
site principal. O IIS, por outro lado, fornece a funcionalidade para que
os hosts virtuais sejam executados a partir desses diretórios,
fornecendo capacidade de vários sites.

Devido às diferentes limitações de funcionalidade, o PWS não possui o
"Assistente de permissões", pois é determinado que não é necessário.
Apenas um usuário estará usando o servidor PWS. No IIS, muitos usuários
usarão o servidor, portanto, são necessárias atribuições de permissão
diferentes.

Depois que a conta "Todos" é removida, o IIS do Windows fica com a conta
" IUSR\_\* " com direitos de nível superior para os diretórios do
servidor web. Uma verificação de permissões ,agora, deve gerar
resultados diferentes. Apenas a conta IUSR\_\* tem permissões totais e
outros usuários devem adquirir o direito "somente leitura" ou nenhum
direito. Os direitos são determinados por quais outros usuários foram
atribuídos a quais direitos aos diretórios do IIS manualmente.

##### Atribuindo permissões

A atribuição de permissões no Windows é razoavelmente simples, mas às
vezes pode ser um pouco confusa. Clique com o botão direito do mouse na
pasta ou arquivo apropriado. Selecionar "Propriedades" ou
"Compartilhamento e segurança" entrará no painel Gerenciamento de
segurança do Windows. Selecionar (clicar uma vez) qualquer nome de
usuário listado exibirá os direitos que o usuário possui na metade
inferior do painel. Alguns direitos podem estar "acinzentados". Eles
estão indisponíveis porque o usuário atual (que você está conectado
como) não tem permissões altas o suficiente para alterá-los ou são
herdados do diretório acima e foram configurados para usar as permissões
desse diretório de nível superior (geralmente é o mecanismo padrão).

Como você pode ver, o Windows utiliza o seguinte esquema de
permissões/direitos:

<table data-cellpadding="2" data-cellspacing="0" data-align="center"
data-border="1" width="533">

<tbody>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p>1. </p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Controle
total</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Permite:
1, 2, 3, 4, 5, 6, 7</p></td>
</tr>
<tr class="even">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 2.</p></td>
<td style="text-align: left;" width="33%"
data-valign="top"><p> Modificar</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Permite:
2, 3, 4, 5, 6</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 3.</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p> Ler e
executar</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Permite:
3, 4 </p></td>
</tr>
<tr class="even">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 4.</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p> Listar
conteúdo da pasta</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Permite:
4 (mas não pode executar programas) </p></td>
</tr>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 5.</p></td>
<td style="text-align: left;" width="33%"
data-valign="top"><p> Ler</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Permite:
5 (implica: 4)<br />
</p></td>
</tr>
<tr class="even">
<td style="text-align: left;" width="5%"
data-valign="top"><p> 6.</p></td>
<td style="text-align: left;" width="33%"
data-valign="top"><p> Gravar</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Permite:
6 (implica:4)<br />
</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;" width="5%"
data-valign="top"><p>7.</p></td>
<td style="text-align: left;" width="33%"
data-valign="top"><p> Permissões especiais</p></td>
<td style="text-align: left;" width="33%" data-valign="top"><p>Permite:
Combinações </p></td>
</tr>
</tbody>
</table>

##### Propriedades de permissões de arquivo do Windows

As permissões de arquivo do Windows podem ser vistas como tendo
propriedades **semelhantes** às permissões de arquivo (modos) do UNIX ou
Linux, elas são apenas representadas de forma diferente. Por exemplo, se
você é principalmente um usuário Unix/Linux, provavelmente está
acostumado a ter permissões representadas como 644/666 755/777, em vez
de serem descritas nos termos acima. Então, quando você é cotado para
usar 644, isso equivale a:

   O proprietário deste arquivo pode ler e gravar nele.

   O grupo do proprietário pode ler o arquivo.

   Todos os outros podem ler o arquivo.

**\* Observação:** *As permissões do Windows e do Unix (listas de
controle de acesso) não equacionam exatamente, pois o Windows não usa o
mecanismo "Grupos" da mesma maneira. No entanto, para esta discussão e
no que diz respeito ao ambiente de hospedagem na web eles podem ser
equacionados sumariamente.** ***

***Ah, mas***,  no Windows "***Grupos***" não são usados e "***Todos***"
deveria ter sido removido.....

Então é aqui que o Windows e o Unix não se igualam, mas o que pode ser
feito é "corresponder" ou "correlacionar" significados equivalentes.
Portanto, este esboço não fornecerá um guia de permissões específico do
Windows ou do NTFS, mas mais uma compreensão de como as permissões
numeradas de estilo UNIX/Linux comumente citadas se correlacionam em uma
máquina com um NTFS.

 
Os arquivos que são colocados na pasta raiz www ou public_html, ou em
qualquer diretório para o qual seu site (www.domain.com.au ou localhost)
aponta em seu disco rígido, devem ser de propriedade de sua conta de
usuário, mas somente se esse usuário não for o que é considerado um
usuário privilegiado como "Administrador" no Windows ou "root" no
UNIX/Linux. Essas contas permitem muito acesso e nunca devem ser usadas
para uso diário.

##### Práticas recomendadas

As práticas de segurança comumente usadas sugerem que todos os
**arquivos** devem ter as seguintes permissões.

       **Proprietário  :**  Ler e gravar

       **Grupo   :**  Somente leitura

       **Outros :** Apenas leitura


    **Todos os diretórios/pastas** devem ter as permissões a seguir.

       **Proprietário  :** Ler, gravar e executar

       **Grupo   :** Ler e executar

       **Outros :** Ler e executar


*Indiscutivelmente, isso não é necessariamente a segurança "ótima", mas
um equilíbrio deve ser alcançado entre segurança, funcionalidade e
capacidade de manutenção.*

O Windows, ao contrário do Unix, não mantém uma única ACL para
"Executar", mas simplesmente fornece "Ler e executar" combinados, o que
não implica em "Gravar". No entanto, a ACL "Ler e executar" implica
"Listar conteúdo do diretório". Portanto, se você tiver apenas
permissões de "Ler" e "Gravar" em um diretório, mas não de "Executar",
não poderá ver o conteúdo do diretório e também poderá ter problemas ao
tentar executar o arquivo por meio de um navegador web.


Infelizmente, é necessário um pouco de compreensão das permissões do
UNIX/Linux para equacioná-las/correlacioná-las totalmente com as
permissões do Windows, a seguinte "folha de dicas" deve ajudar;

 

<table data-cellpadding="2" data-cellspacing="0" data-align="center"
data-border="1" width="659">

<tbody>
<tr class="odd">
<td style="text-align: center;" data-bgcolor="#cccccc" width="7%"
data-valign="top"><p><strong>Unix Mode</strong></p></td>
<td data-bgcolor="#cccccc" width="10%"
data-valign="top"><p><strong>Windows ACL </strong></p></td>
<td data-bgcolor="#cccccc" width="33%"
data-valign="top"><p><strong>Comentários </strong></p></td>
</tr>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>7 </strong></p></td>
<td width="10%"
data-valign="top"><p><strong> Modificar </strong></p></td>
<td width="33%" data-valign="top"><p><em>Ler, escrever e executar, você
deve ser o proprietário deste arquivo<br />
</em></p></td>
</tr>
<tr class="odd">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>6</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Ler e gravar<br />
</strong></p></td>
<td width="33%" data-valign="top"><p><em> </em></p></td>
</tr>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>5</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Ler e executar<br />
</strong></p></td>
<td width="33%" data-valign="top"><p><em>usado para a maioria das
aplicações<br />
</em></p></td>
</tr>
<tr class="odd">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>4</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Somente leitura<br />
</strong></p></td>
<td width="33%" data-valign="top"><p><em>segurança através da
obscuridade não é uma boa prática<br />
</em></p></td>
</tr>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>3</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Gravar e executar<br />
</strong></p></td>
<td width="33%" data-valign="top"><p><em>não disponível através do
Windows, a menos que permissões "especiais" sejam usadas, não usada
comumente<br />
</em></p></td>
</tr>
<tr class="odd">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>2</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Apenas gravar<br />
</strong></p></td>
<td width="33%" data-valign="top"><p><em>não está disponível através do
Windows, a menos que permissões "especiais" sejam usadas, não usada
comumente<br />
</em></p></td>
</tr>
<tr class="even">
<td style="text-align: center;" width="7%"
data-valign="top"><p><strong>1</strong></p></td>
<td width="10%" data-valign="top"><p><strong> Apenas executar<br />
</strong></p></td>
<td width="33%" data-valign="top"><p><em>(não está disponível através do
Windows, a menos que permissões "especiais" sejam usadas, não usada
comumente)<br />
</em></p></td>
</tr>
</tbody>
</table>



Então, como um exemplo de comparação com os modos do Unix, quando você é
citado algo como 644, agora você precisa dividir isso em três entidades:

      **6**  :  **4**  : **4**

O primeiro número representa as permissões dos "**Proprietários**", o
segundo representa as permissões do "**Grupo**" e a terceira, as
permissões dos "**Outros**".


Assim, o equivalente do Windows seria algo como;

  **Owner** (6) : **Ler e gravar**

  **Group** (4) : **Apenas ler**

  **Others** (4) : **Apenas ler**

 

Felizmente, este exemplo fornece algumas dicas sobre como correlacionar
modos/permissões do Unix em permissões/ACLs do Windows. Este documento
não inclui assuntos mais complexos, como permissões "efetivas",
"herdadas" ou "especiais". Apesar da facilidade de uso do Windows, os
mecanismos de permissões e ACLs da Microsoft são razoavelmente complexos
e muito extensos, mas isso pode fornecer uma referência rápida para
tentar aliviar um pouco da confusão em torno das traduções de permissões
do Unix e do Windows.
