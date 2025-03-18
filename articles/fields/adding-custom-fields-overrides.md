<!-- Filename: J3.x:Adding_custom_fields/Overrides / Display title: Substituições de Modelo -->

## Exibição Automática de Campo

Cada um dos campos disponíveis tem uma opção chamada *Exibição Automática* que pode ser configurada para uma das seguintes opções:

* Após o Título
* Antes do Conteúdo Exibido
* Após o Conteúdo Exibido
* Não exibir automaticamente

Se a última dessas opções for selecionada, o campo não será exibido, a menos que você crie uma substituição de template para gerenciar a exibição por conta própria. Ou você pode adicionar `{field ID}` em um artigo para colocar o campo onde preferir. Mas é necessário lembrar de fazer isso em cada artigo.

Este exemplo mostra como criar uma substituição de template para um Contato. Os métodos também se aplicam aos componentes de Conteúdo e Usuário.

## Criar uma Substituição de Modelo

No menu do Administrador:

* Selecione **Sistema / Modelos de Site / Detalhes e Arquivos do Cassiopeia**
* Selecione a aba **Criar Substituições**.
* Selecione **com_contact** no painel de *Componentes*
* Selecione **Contato** na lista de visualizações disponíveis. Este é o layout para
um único contato.

No painel **Editor**:
* Selecione **html / com_contact / contact / default.php**, que é o arquivo
que define o layout geral da página de contato única.
* Role para baixo neste arquivo e observe uma série de blocos `<php if (...) : ?>`.
Cada um irá mostrar ou ocultar uma seção de texto dependendo das configurações de contato.
* Observe as linhas contendo
```
    <?php echo $this->item->event->afterDisplayTitle; ?> (linha 73)
    <?php echo $this->item->event->beforeDisplayContent; ?> (linha 98)
    <?php echo $this->item->event->afterDisplayContent; ?> (linha 189)
```
Uma destas variáveis, ou nenhuma delas, é populada dependendo do valor do campo de
Exibição Automática.

## Usando campos na sua substituição

Você tem todos os campos correspondentes ao item atual acessíveis através da
propriedade `$this->item->jcfields`, que é um array que contém os seguintes
dados para cada campo (este exemplo é para um campo Editor):

```php
    Array
    (
        [4] => stdClass Object
            (
                [id] => 4
                [title] => article-editor
                [name] => article-editor
                [checked_out] => 0
                [checked_out_time] => 0000-00-00 00:00:00
                [note] =>
                [state] => 1
                [access] => 1
                [created_time] => 2017-04-07 12:08:59
                [created_user_id] => 856
                [ordering] => 0
                [language] => *
                [fieldparams] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [buttons] =>
                                [width] =>
                                [height] =>
                                [filter] =>
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [params] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [hint] =>
                                [render_class] =>
                                [class] =>
                                [showlabel] => 1
                                [disabled] => 0
                                [readonly] => 0
                                [show_on] =>
                                [display] => 2
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [type] => editor
                [default_value] =>
                [context] => com_content.article
                [group_id] => 0
                [label] => article-editor
                [description] =>
                [required] => 0
                [language_title] =>
                [language_image] =>
                [editor] =>
                [access_level] => Público
                [author_name] => Super Usuário
                [group_title] =>
                [group_access] =>
                [group_state] =>
                [value] => Bar
                [rawvalue] => Bar
            )
    )
```

## Renderizar o campo

A função `FieldsHelper::render()` é usada para renderizar cada campo. Primeiro, adicione uma declaração `use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;` à lista de declarações `use` no topo do arquivo de substituição:

```php
defined('_JEXEC') or die;

use Joomla\CMS\Helper\ContentHelper;
use Joomla\CMS\HTML\HTMLHelper;
use Joomla\CMS\Language\Text;
use Joomla\CMS\Layout\FileLayout;
use Joomla\CMS\Layout\LayoutHelper;
use Joomla\CMS\Plugin\PluginHelper;
use Joomla\CMS\Router\Route;
use Joomla\Component\Contact\Site\Helper\RouteHelper;
use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;
```

Então, onde você desejar inserir os campos no seu template, use o seguinte código:
```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo FieldsHelper::render($field->context, 'field.render', array('field' => $field)); ?><br>
<?php endforeach ?>
```

Ou para uma substituição pura, que não traduz o rótulo:

```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo $field->label . ':' . $field->value; ?><br>
<?php endforeach ?>
```

## Carregando campos individuais

Para adicionar campos individuais ao seu conteúdo, comece escolhendo nomes específicos para seus campos personalizados, usando o campo **Nome**, que será usado para referenciar seu campo diretamente no código de substituição. Na aba `Opções`, selecione **Não** no campo `Exibição Automática` para evitar que o campo seja exibido automaticamente em qualquer uma das posições padrão.

Em seguida, para permitir acesso direto por nome aos campos personalizados em uma substituição, coloque o código abaixo no início do seu arquivo. Você deve fazer isso em cada arquivo PHP de substituição em que queira colocar campos personalizados individuais.

```php
<?php foreach($this->item->jcfields as $jcfield) {
    $this->item->jcFields[$jcfield->name] = $jcfield;
} ?>
```

E por último, você deve adicionar o código de colocação do campo no local onde deseja que o rótulo ou o valor do campo sejam exibidos.

Para adicionar o **rótulo** do campo à sua substituição, insira o código abaixo, substituindo `name-of-field` pelo nome do campo.

```php
<?php echo $this->item->jcFields['name-of-field']->label; ?>:&nbsp;
```

Para adicionar o **valor** do campo à sua substituição, insira o código abaixo, substituindo `name-of-field` pelo nome do campo.

```php
<?php echo $this->item->jcFields['name-of-field']->rawvalue; ?>
```

Você pode adicionar este código a qualquer parte da sua substituição. Exemplos: O conteúdo de uma div, o src em uma tag `img`, dentro de um atributo de classe CSS, etc.
