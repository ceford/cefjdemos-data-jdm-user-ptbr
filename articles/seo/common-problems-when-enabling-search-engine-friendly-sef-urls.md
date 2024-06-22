<!-- Filename: Common_problems_when_enabling_Search_Engine_Friendly_(SEF)_URLs / Display title: Problemas comuns ao habilitar localizadores uniformes de recursos (URLs) amigáveis para mecanismos de pesquisas (SEFs) -->

A ativação de localizadores uniformes de recursos (URLs) amigáveis para
mecanismos de pesquisas (SEFs) pode causar problemas se a hospedagem do
seu site não estiver configurada corretamente para oferecer suporte à
regravação de localizadores uniformes de recursos (URLs). Existem muitas
combinações diferentes de tecnologias de servidor e sistemas
operacionais, portanto, não é possível dar respostas definitivas para
todos os problemas com localizadores uniformes de recursos (URLs)
amigáveis para mecanismos de pesquisas (SEFs), no entanto, alguns dos
problemas mais comuns estão listados abaixo.

## Seu servidor está executando o Apache?

Quando você habilita localizadores uniformes de recursos (URLs)
amigáveis para mecanismos de pesquisas (SEFs) no Joomla! existe uma
opção para reescrever os localizadores uniformes de recursos (URLs) sem
o /index.php/ que requer o mod_rewrite (ou o equivalente do IIS) - se o
seu servidor não estiver executando o Apache ou não tiver a capacidade
de reescrever os localizadores uniformes de recursos (URLs) dessa
maneira, haverá mensagens de erro com esta opção habilitada. Tente mudar
esta opção para "não" e veja se este método de reescrita funciona para
você.

Certifique-se também de que você tenha uma seção de "diretório" em seu
arquivo de configuração do Apache que permita substituições do
.htaccess, caso contrário o arquivo .htaccess em seu diretório raiz do
Joomla! será ignorado. A diretiva necessária é:

     AllowOverride all

## Seu servidor está executando o IIS?

Se você estiver usando o IIS, confira esses links que podem ser úteis:

- IIS
- <a href="https://docs.joomla.org/IIS6_and_SEF_URLs_using_Joomla_1.5x"
  class="mw-redirect" title="IIS6 and SEF URLs using Joomla 1.5x">IIS6 e
  localizadores uniformes de recursos (URLs) amigáveis para mecanismos de
  pesquisas (SEFs) usando o Joomla 1.5x</a>
- <a href="https://docs.joomla.org/IIS7_and_SEF_URLs_using_Joomla_1.5x"
  class="mw-redirect" title="IIS7 and SEF URLs using Joomla 1.5x">IIS7 e
  localizadores uniformes de recursos (URLs) amigáveis para mecanismos de
  pesquisas (SEFs) usando o Joomla 1.5x</a>

*Os três links acima estão disponíveis apenas em inglês.*

## Você limpou seu cache?

Ao fazer qualquer alteração nas configurações dos localizadores
uniformes de recursos (URLs) amigáveis para mecanismos de pesquisas
(SEFs), é aconselhável certificar-se de limpar o cache e, se estiver
armazenando localizadores uniformes de recursos (URLs) em cache (por
exemplo, usando uma extensão para localizadores uniformes de recursos
(URLs) amigáveis para mecanismos de pesquisas (SEFs) de terceiros),
certifique-se de alterar as configurações e limpar os localizadores
uniformes de recursos (URLs) em cache se necessário.

## Você moveu domínios?

Às vezes, se você alterou os domínios (por exemplo, de um host local ou
ambiente de teste para o domínio ativo), precisará editar o valor da
variável `$live_site` no arquivo configuration.php encontrado no
diretório raiz dos arquivos do seu site Joomla. O valor da variável deve
ser editado manualmente, não pode ser acessado pelas telas de
configurações globais.

Normalmente, ficaria assim:

    var $live_site = 'http://example.com';

Ou, se você acessa seu site em uma subpasta chamada joomla, ficaria
assim:

    var $live_site = 'http://example.com/joomla';

Quando você move domínios, esse valor pode precisar ser atualizado para
refletir seu novo nome de domínio:

    var $live_site = 'http://mynewdomain.com';

Muitas vezes, não há necessidade de especificar esta variável - em que
lugar simplesmente deixe em branco:

    var $live_site = '';

Often, there is no need to specify this variable at all - in which place
simply leave it blank:

    var $live_site = '';

- Consulte o <a
  href="http://www.scribd.com/doc/2300167/Joomla-v-15-Configure-and-troubleshoot-SEF-URLs"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Scribd</a> de
  <a href="https://docs.joomla.org/GHOP_students/Benjamin_H%C3%A4ttasch"
  class="mw-redirect" title="GHOP students/Benjamin Hättasch">Benjamin
  Hättasch</a> que contém passos instruções passo a passo para instalar
  e solucionar problemas de seus localizadores uniformes de recursos
  (URLs) amigáveis para mecanismos de pesquisas (SEFs).
