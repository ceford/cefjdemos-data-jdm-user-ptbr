<!-- Filename: Template_Considerations_During_Migration / Display title: Considerações Sobre Templates Durante a Migração -->

<img
src="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/25px-Copyedit.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/38px-Copyedit.png 1.5x, https://docs.joomla.org/images/thumb/4/47/Copyedit.png/50px-Copyedit.png 2x"
data-file-width="200" data-file-height="200" width="25" height="25"
alt="Copyedit.png" />This Article Needs Your Help

*This article is tagged because it* **NEEDS UPDATING***. You can help
the Joomla! Documentation Wiki by <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Template_Considerations_During_Migration/pt-br&amp;action=edit"
class="external text" target="_blank"
rel="noreferrer noopener">contributing to it</a>.
<span class="small">More pages that need help similar to this one are
here.</span>
<span class="small">**NOTE-If you feel the need is satistified, please
remove this notice.**</span>*
**Reason:** See section 3.4 and 4

Às vezes os templates deixam as pessoas andando em círculos durante uma
migração. Não precisa ser assim. Com uma pequena explicação, as coisas
podem ficar claras quanto às suas opções.

## Introdução

Os templates são uma extensão, assim como componentes, módulos e plugins
são também são.

Na configuração da migração, você precisará decidir o que fazer com o
seu template atual (que determina a "aparência" atual do seu site).

Na maioria dos casos a situação do template se encaixa em uma das opções
abaixo:

- Você está usando um template que foi comprado de um clube de modelos.
- Você está usando um template que foi uma compra única de algum
  provedor de templates.
- Você tinha um template personalizado projetado para você.
- Você está usando um template padrão que veio com sua instalação do
  Joomla (os modelos padrão do Joomla! 1.5 são os modelos padrão
  Rhuk_milkyway, JA Purity, Beez e do Joomla! 2.5 são Atomic e duas
  versões diferentes do Beez). O template pode ter sido personalizado
  significativamente ou não.

## Avaliando o cenário do template

Antes de decidir o que fazer, você pode querer avaliar se deseja manter
o aspecto atual do seu site atual. Se você quer uma mudança, este é o
momento de decidir isso. Talvez o maior motivo pelo qual você queira
mudar o seu template é utilizar a tecnologia mais recente encontrada nos
template atuais. Os template responsivos não estavam disponíveis na
versão 1.5 (a menos que você tenha contratado recentemente alguém para
tornar seu template 1.5 amigável para dispositivos móveis) e mesmo no
início do ciclo de vida 2.5, as versões móveis dos modelos eram simples
e a ainda não havia responsividade.

Vamos avaliar esses cenários um por vez:

### You are using Protostar

Protostar is not compatible with Joomla 4.x. The migration will work on
the one-click from Joomla 3.10.x to 4.x but the template will disappear
and be replaced with Cassiopeia upon migration. You will need to plan on
using Cassiopeia or some other template in Joomla 4.

#### Why can't you carry forward Protostar into Joomla 4?

Protostar is based on an old version of Bootstrap (Bootstrap 2) and
jQuery (1.x). The versions of these components are outdated and have
known security issues (Joomla 3 maintained forked versions of these
libraries with security patches applied) - and Joomla 4 has updated
these to the latest version - Bootstrap 5. However this means that
templates need to be updated to use the new HTML syntax that Bootstrap 5
requires.

### Você está usando um template comprado em um clube de templates

Este é o mais fácil - na maioria das vezes. Se você comprou um template
de um clube de templates, entre em contato a empresa e veja se eles
possuem uma versão do seu template para o Joomla 3.x. Se sim, ótimo, mas
existem algumas coisas a ponderar. Se o site atual está na versão 1.5 e
está migrando para 3.x, verifique se a versão do Joomla 3 é responsiva,
se isso for importante para você claro. Se você estiver indo da versão
1.5 para 3, as chances são boas de que haverá algumas diferenças no
template em relação às versões 1.5 do e 3 do template. Esteja preparado
para fazer algumas personalizações no template se você deseja que ele
pareça "exatamente" o mesmo.

Se você estiver migrando da versão 2.5 para 3.x, verifique se as versões
2.5 e 3.x são embutidas no mesmo pacote do desenvolvedor. Se não
estiverem, verifique com o desenvolvedor as etapas para atualizar do
Joomla 2.5 para 3.x. Se 2,5 e 3.x estiverem no mesmo pacote, você foi
premiado. Se não estiverem, você ainda pode ter sorte. Depende apenas da
agenda de atualização do desenvolvedor.

### Você está usando um template adquirido numa compra única de algum provedor de templates

Se você comprou um template de um provedor de templates numa compra
única, verifique com a empresa se existe uma versão disponível para o
Joomla 3.x. Se não houver, provavelmente você está sem sorte. No
entanto, você pode tentar entrar em contato com alguém da empresa para
ver se eles podem atualizá-lo para você e torná-lo compatível com o
Joomla 3.x.

Se isso falhar, então você precisará:

1.  Escolha um novo template.
2.  Converta o template para ser compatível com o Joomla 3.x. (Nota:
    pode não ser responsivo).

O item 1 é auto-explicativo. Você pode escolher um template de um
fornecedor comercial ou personalizar o template padrão do Protostar
(veja mais no Protostar abaixo) que é instalado com o Joomla 3.x. O item
2 não é tão simples. Para converter seu modelo existente para ser
compatível com o Joomla 3, consulte a seção a seguir.

## Conversões de Template ou Migrações de Template

### Conversões de Template 1.5 para 3

-  Migrating a Template from Joomla 1.5 to
  3.x

### Conversões de Template 1.5 para 2.5

-  Upgrading a Joomla 1.5 template to Joomla
  2.5
- <a
  href="http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25"
  class="external free" target="_blank"
  rel="noreferrer noopener">http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25</a>

### Conversões de Template 2.5 para 3

-  J3.x:Converting A Previous Joomla! Version
  Template
- <a
  href="http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0</a>
- <a href="https://www.youtube.com/watch?v=E13QMWgvwlA"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://www.youtube.com/watch?v=E13QMWgvwlA</a>

### 3.10.x to 4 Template Conversions

This section needs content. If you have knowledge on converting
templates built for Joomla 3 to make them compatible with Joomla 4,
please write a magazine article or post a YouTube or something that can
be linked from this area. Thanks in advance.

### Você tem um template personalizado projetado para você

Se você tem um template personalizado projetado para o seu site 1.5 ou
2.5, ele precisará ser convertido para ser compatível com Joomla 3. Veja
os links na seção anterior. Se você precisa contratar alguém para
converter seu template existente para ser compatível com o Joomla 3.x,
confira o Diretório de Recursos Joomla! em
<a href="http://resources.joomla.org/en/category/custom-templates"
class="external text" target="_blank" rel="noreferrer noopener">Template
Development</a> ou as categorias <a
href="http://resources.joomla.org/en/category/migration-and-upgrade-services"
class="external text" target="_blank"
rel="noreferrer noopener">Migrations &amp; Upgrades</a>.

### Você está usando um template padrão fornecido com sua instalação do Joomla

Joomla! 1.5 templates padrão são Rhuk_milkyway, JA Purity e Beez.
Joomla! 2.5 modelos padrão são Atomic e duas versões diferentes do Beez.
Pode ter sido personalizado significativamente ou não. Se você estiver
usando um template padrão 2.5 e indo para Joomla 3.x, você poderá fazer
uma atualização de um clique. Se você estiver usando um template padrão
1.5, então você precisará passar por uma das etapas acima para
atualizá-lo para o Joomla 3.x. (Se alguém encontrar essas informação
incorreta, contribua e corrija isso).

Antes de decidir se deseja converter seu template 1.5 para o Joomla 3,
você pode considerar seriamente considerar um novo template semelhante
ao seu template existente. As chances são de que será mais barato e mais
rápido usar um novo, depois converter o antigo. Se você deseja converter
o antigo e não tem as habilidades para fazê-lo você mesmo, visite o <a
href="http://resources.joomla.org/pt/category/migration-and-upgrade-services,"
class="external text" target="_blank" rel="noreferrer noopener">Joomla!
Resource Directory ™</a>.

Protostar, the template that ships with Joomla 3.x is **not** compatible
with Joomla 4.x. You will need to go through one of the steps above to
update it for Joomla 4.x.

### Ao escolher templates

- Apenas olhe para uma empresa de templates por vez, ou se torna
  cansativo;
- Se você começar a ficar sobrecarregado, faça uma pausa mesmo que isso
  signifique continuar noutro dia;
- Tente olhar além das demonstrações animadas e chamativas. Você estará
  colocando seu conteúdo no template, e não fazendo tudo o que o
  template é capaz;
- Veja as posições dos módulos e as variações dos template;
- Beber bastante água enquanto procura por modelos e esticar cada hora
  ou mais.

## Usando o template padrão do Protostar no Joomla 3.x

Esta seção está incompleta. Se você tiver conhecimento sobre este
tópico, participe adicionando neste documento. Entretanto, uma busca do
Google na personalização do Protostar irá gerar muitos resultados fora
do Joomla! Docs.
