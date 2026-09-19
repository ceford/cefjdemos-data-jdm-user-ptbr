<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Manter os submenus abertos",
    "description": " ",
    "author": ""
}
-->

Um módulo de menu pode ser usado para exibir um menu horizontal (geralmente no topo da página) ou um menu vertical (geralmente em uma barra lateral, à esquerda ou à direita). Em um menu horizontal (superior), não é desejável manter o submenu aberto. É por isso que o comportamento padrão de um módulo de menu é fechar os submenus ao carregar a página.

## Comportamento de alternância do status *aberto*

No entanto, em um menu vertical (na barra lateral), geralmente é desejável deixar um submenu aberto quando ele contém o item de menu ativo. No Joomla 6.0, uma nova classe CSS, `nav-active-open`, foi introduzida especificamente para permitir o controle sobre se os submenus devem ser abertos automaticamente ao carregar a página para o item de menu ativo. Definir essa classe agora torna isso possível. A classe é definida no módulo por meio do painel administrativo.

![configuração da classe do menu no painel administrativo para nav-active-open para manter a alternância aberta no menu ativo](../../../en/images/menus/keep-submenus-open/01-menu-class-setting.png)

## Como criar um menu de barra lateral sem alternância suspensa

Se você quiser manter todos os submenus abertos, não precisará de uma alternância suspensa. Em vez disso, use uma [substituição de template](jdocmanual?article=user/templates/template-overrides).

Veja como essa substituição específica de template é feita:

1. Comece selecionando Sistema → Templates → Templates do site no menu do Administrador e, em seguida, selecione o item Detalhes e arquivos do Cassiopeia. Isso abrirá o formulário Templates: Personalizar (Cassiopeia).

2. Alterne para a aba Criar substituições e selecione mod_menu:

![seleção da substituição do template do módulo de menu](../../../en/images/menus/keep-submenus-open/02-create-override-select-mod-menu.png)

Isso copiará todos os arquivos de layout do menu do módulo de menu para a substituição. Em seguida, você retornará à aba Editor.

3. Na aba Editor, expanda as entradas em HTML → mod_menu.  Aqui você encontrará o arquivo `default.php`. Abra o arquivo e copie seu conteúdo para um local seguro. Feche o arquivo.

4. Crie um novo arquivo na pasta html → mod_menu. Ele deve ter um nome que não inclua um sublinhado. Neste exemplo, o novo arquivo se chama `treedefault.php`. Isso permite selecionar o layout de menu padrão ou esse layout de menu alternativo em qualquer um dos seus módulos de menu. Na lista de arquivos de substituição a seguir, o original está contornado em vermelho e a nova alternativa está contornada em verde.

![aba de edição da substituição de mod_menu - abrir default.php](../../../en/images/menus/keep-submenus-open/03-edit-mod-menu.png)

4. Edite o novo arquivo de layout. As etapas a seguir estão listadas na ordem inversa para
preservar os números das linhas durante o processo de edição:

Altere a linha 104 para que ela contenha o seguinte:

```
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
```

Isso mantém o menu aberto e adiciona recuo aos submenus.

Substitua as linhas 98 - 101 por `break`

```php
                    echo '<button class="mod-menu__toggle-sub" aria-expanded="false">' .
                 break;
                    '<span class="icon-chevron-down" aria-hidden="true"></span>' .
                    '<span class="visually-hidden">' . Text::sprintf('MOD_MENU_TOGGLE_SUBMENU_LABEL', $item->title) . '</span>' .
                    '</button>';
```

Remova as linhas 93 - 94

```php
                    echo '<span class="icon-chevron-down" aria-hidden="true">' .
                        '</span></button>';
```

Remova as linhas 66-71

```php
    // The next item is deeper - add toggle only here it is a heading or separator
    if ($item->deeper && (int) $item->level === $startLevel && in_array($item->type, ['separator', 'heading'])) {
        // Add a toggle button.
        echo '<button class="mod-menu__toggle-sub" aria-expanded="false">';
    }
```

Remova as linhas 15 - 20

```php
/** @var Joomla\CMS\WebAsset\WebAssetManager $wa */
$wa = $app->getDocument()->getWebAssetManager();
$wa->getRegistry()->addExtensionRegistryFile('mod_menu');
$wa->usePreset('mod_menu.menu');
```

Este é o arquivo completo de substituição `treedefault.php`:

```
<?php

/**
 * @package     Joomla.Site
 * @subpackage  mod_menu
 *
 * @copyright   (C) 2009 Open Source Matters, Inc. <https://www.joomla.org>
 * @license     GNU General Public License version 2 or later; see LICENSE.txt
 */

defined('_JEXEC') or die;

use Joomla\CMS\Helper\ModuleHelper;
use Joomla\CMS\Language\Text;

$tagId      = $params->get('tag_id', '') ?: 'mod-menu' . $module->id;
$id         = ' id="' . htmlspecialchars($tagId, ENT_QUOTES, 'UTF-8') . '"';
$startLevel = (int) $params->get('startLevel', 1);

// The menu class is deprecated. Use mod-menu instead
?>
<ul<?php echo $id; ?> class="mod-menu mod-list nav <?php echo $class_sfx; ?>">
<?php foreach ($list as $i => &$item) {
    $itemParams = $item->getParams();
    $class      = 'nav-item item-' . $item->id;

    if ($item->id == $default_id) {
        $class .= ' default';
    }

    if ($item->id == $active_id || ($item->type === 'alias' && $itemParams->get('aliasoptions') == $active_id)) {
        $class .= ' current';
    }

    if (in_array($item->id, $path)) {
        $class .= ' active';
    } elseif ($item->type === 'alias') {
        $aliasToId = $itemParams->get('aliasoptions');

        if (count($path) > 0 && $aliasToId == $path[count($path) - 1]) {
            $class .= ' active';
        } elseif (in_array($aliasToId, $path)) {
            $class .= ' alias-parent-active';
        }
    }

    if ($item->type === 'separator') {
        $class .= ' divider';
    }

    if ($item->deeper) {
        $class .= ' deeper';
    }

    if ($item->parent) {
        $class .= ' parent';
    }

    echo '<li class="' . $class . '">';

    switch ($item->type) :
        case 'separator':
        case 'component':
        case 'heading':
            require ModuleHelper::getLayoutPath('mod_menu', 'default_' . $item->type);
            break;
        default:
            require ModuleHelper::getLayoutPath('mod_menu', 'default_url');
            break;
    endswitch;

    // The next item is deeper.
    if ($item->deeper) {
        // Check type - add only on first level
        // @todo aria-label - set in menu item ???
        if ((int) $item->level === $startLevel) {
            switch ($item->type) {
                case 'heading':
                case 'separator':
                    break;

                default:
                    break;
            }
        }
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
    } elseif ($item->shallower) {
        // The next item is shallower.
        echo '</li>';
        echo str_repeat('</ul></li>', $item->level_diff);
    } else {
        // The next item is on the same level.
        echo '</li>';
    }
}
?></ul>
```

## Resultado

O resultado é uma lista simples, sem a funcionalidade de alternância para o módulo de menu lateral, ilustrada aqui à esquerda:

![resultado com substituição de template - lista simples sem botões e funcionalidade de alternância](../../../en/images/menus/keep-submenus-open/05-site-result.png)

*Traduzido por openai.com*
