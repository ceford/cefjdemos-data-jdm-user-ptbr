<!-- Filename: Entering_raw_HTML_in_editors / Display title: Filtros HTML -->

## Tag Textarea do HTML

Em HTML, um campo de entrada de múltiplas linhas é conhecido como textarea. Qualquer texto entre as tags de abertura e fechamento é exibido como texto que pode conter marcação HTML.
Exemplo:
```
<textarea><p class="poem">A rápida raposa marrom<br>
pula sobre o cão preguiçoso.</textarea>
```
Editores, como TinyMCE ou Code Mirror, usam JavaScript para sobrepor a textarea com uma exibição diferente, permitindo a entrada de dados WYSIWYG e/ou realce de sintaxe. O botão de alternância abaixo de um campo de editor alterna entre a visão de textarea e a visão WYSIWYG.

Visões de editor são usadas para o conteúdo de Artigos e alguns Módulos. No entanto, você precisa estar ciente de que nem todas as tags e atributos HTML (como class="xyz") são permitidos para todos os usuários. Alguns ou todos podem desaparecer quando você salva o conteúdo de uma textarea ou campo de edição.

Isso é causado por mecanismos de filtragem, seja na Configuração Global do Joomla! ou na configuração do editor. Um filtro de editor pode ser contornado selecionando *Sem Editor* nas suas configurações de *Perfil de Usuário*. Você não pode contornar os filtros globais, mas pode alterá-los para atender aos propósitos do seu site.

## Seleção de Editor pelo Usuário

Você pode selecionar um dos editores disponíveis, incluindo Nenhum, no seu Perfil de Usuário, acessível através do menu Conta do Usuário / Editar Perfil no canto superior direito da tela do Administrador. O formulário Editar: Perfil contém uma aba de Configurações Básicas com um campo para selecionar um Editor. Normalmente, está definido como *- Usar Padrão -*, que geralmente é o TinyMCE. Você pode selecionar *Editor Nenhum*. Isso vai ignorar qualquer filtragem de tags HTML e atributos não permitidos pelas configurações de configuração do TinyMCE.

**Aviso:** se você selecionar *Editor - Nenhum* para criar conteúdo contendo tags HTML proibidas por um filtro de editor e depois voltar ao editor padrão, deve ter cuidado para não editar e salvar esse conteúdo novamente, ou perderá qualquer tag e atributo filtrado. É fácil fazer isso por engano e não há aviso.  

## Configuração Global: Filtros de Texto

No Painel Inicial, selecione Configuração Global e depois a aba Filtros de Texto. As configurações padrão têm *Sem HTML* selecionado para os grupos de usuários Visitante, Público e Registrado. Qualquer um desses grupos pode ter a oportunidade de preencher um campo de área de texto, por exemplo, em um formulário de contato que busca informações adicionais sobre um problema, então a remoção automática de todas as tags HTML é geralmente apropriada. Outros grupos, exceto Super Usuários, são restringidos pela Lista Padrão de Proibidos. Super Usuários não têm filtragem.

![configuração global dos filtros de texto](../../../en/images/configuration/global-configuration-filters-tab.png)

As notas explicam o que está incluído na lista padrão de proibidos e como usar as outras listas.

## Configuração do TinyMCE para Filtros de Texto

Editores são implementados como Plugins no Joomla. O editor CodeMirror não possui configurações de filtro de texto. Para personalizar o editor TinyMCE, encontre e selecione-o na lista de plugins. No meio da longa lista de configurações, você verá um campo denominado *Usar Filtro de Texto do Joomla*, que está **Desligado** por padrão. Os três campos seguintes são:
* **Elementos Proibidos**: uma lista de tags que sempre serão removidas. A lista padrão de *script,applet,iframe* todos têm preocupações de segurança.
* **Elementos Válidos**: use esta lista para limitar as tags válidas a um subconjunto de todas as tags HTML comuns. Exemplo: `a[href|target=_blank],strong/b,div[align],br`
* **Elementos Válidos Estendidos**: use esta lista para adicionar um elemento ao conjunto de regras padrão existente ou para modificar um elemento no conjunto de regras padrão. Exemplo: `img[class|src|border=0|alt|title|hspace|vspace|width|height|align|onmouseover|onmouseout|name]`

Veja a Documentação do TinyMCE para mais explicações.

Para ignorar os filtros de texto do TinyMCE e usar os filtros de texto do Joomla, ajuste *Usar Filtro de Texto do Joomla* para **Ligado**. Os três campos adicionais descritos acima desaparecem, pois não são usados.

