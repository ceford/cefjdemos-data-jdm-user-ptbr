<!--
{
    "source": "https://docs.joomla.org/category-list-override.md",
    "title": "Substitui\u00e7\u00e3o da Lista de Categorias",
    "description": "Saiba como criar uma substitui\u00e7\u00e3o de template para melhorar o layout de uma lista de contatos em uma categoria ",
    "author": ""
}
-->

## A Lista de Contatos em uma Categoria

O layout padrão dos contatos em uma categoria é controlado por um template no 
código do componente com_contacts. O layout padrão é semelhante a este:

![comitê cultural usando o layout e o estilo padrão](../../../en/images/contacts/category-list-override/01-contacts-culture-committee.png)

Pode ser uma opinião pessoal, mas, para mim, o layout padrão dos contatos não é muito 
satisfatório. Meus problemas:

* As imagens de retrato originais tinham 500 pixels de largura e eram dominantes demais.
* O nome do contato não recebe destaque suficiente.
* A lista de detalhes pessoais não tem um título e parece isolada.
* A função do indivíduo não tem um título.
* Os campos de endereço e código postal estão ausentes.
* Os dados de localização estão incompletos.
* Os dados de cada contato são organizados em uma tabela e ficam bastante apertados em telas estreitas.

Então, como corrigir isso de acordo com minha preferência? Minha solução é criar uma substituição de template 
e adicionar alguns estilos personalizados. Este é o resultado:

![comitê empresarial usando uma substituição de template e estilos personalizados](../../../en/images/contacts/category-list-override/02-contacts-business-committee.png)

## Substituição do Layout do Template

A pasta com_contact/tmpl/category contém três arquivos PHP: default.php,
default_children.php e default_items.php. O último desta lista contém
o layout de tabela para a lista.

Os arquivos de substituição são criados em Sistema / Templates do site / Cassiopeia
Detalhes e arquivos / Criar substituições. Selecione com_contact e depois category.
A pasta html então contém com_contact/category com os três arquivos de template
mencionados acima. 

### Altere o arquivo default.php para mydefault.php

O arquivo `default.php` contém uma linha que especifica qual layout usar para 
cada registro individual. Selecione este arquivo para edição e **renomeie-o** para 
`mydefault.php` (ou use qualquer prefixo de sua preferência em vez de `my`). Não use
um sublinhado no nome do arquivo!

Quando você for posteriormente ao formulário Contatos / Categoria / Editar, o campo
Layout da aba Opções permitirá escolher entre o layout do componente e o layout
da sua substituição. Ele se parece com isto:

```
---From Global Options---
  Use Global
---From Component---
  Default
---From cassiopeia Template---
  mydefault

```

### Edite o arquivo mydefault.php

A linha 20 de `mydefault.php` contém `$this->subtemplatename = 'items';`.
Altere `items` para `myitems` para que as linhas 18 a 23 fiquem assim:

```html
<div class="com-contact-category">
    <?php
        $this->subtemplatename = 'myitems';
        echo LayoutHelper::render('joomla.content.category_default', $this);
    ?>
</div>
```

### Altere o arquivo default_items.php para mydefault_myitems.php

O arquivo `default_items.php` contém o layout de cada contato. Ele precisa ser
renomeado para preservar a opção de usar o layout original. A primeira parte do
nome não é importante. É a parte `myitems`, mencionada no arquivo
`mydefault.php`, que é usada para o layout.

### Edite o arquivo mydefault_myitems.php

A seção `<table>...</table>` deste arquivo abrange as linhas 85 a 204. Para a
substituição do layout, substituí a marcação da tabela pela seguinte marcação de
grade do Bootstrap. Em telas estreitas, as três colunas são empilhadas. Em telas
com mais de 768 pixels de largura, as colunas ficam lado a lado. A marcação
revisada moveu os campos personalizados para baixo do nome do contato.

```
<div class="container-fluid text-center border border-2">
<?php $nrows = 0; foreach ($this->items as $i => $item) : ?>
    <?php if ($item->published !== 1 ||
        (!empty($item->publish_up) && strtotime($item->publish_up) > strtotime(Factory::getDate())) ||
        (!empty($item->publish_down) && strtotime($item->publish_down) < strtotime(Factory::getDate()))) { continue; } ?>
        <div class="row cat-list-row<?php echo $nrows % 2; $nrows += 1; ?> align-items-center">
            <div class="col-12 col-md-3">
                <?php if ($this->params->get('show_image_heading')) : ?>
                    <?php if ($item->image) : ?>
                        <?php echo LayoutHelper::render(
                            'joomla.html.image',
                            [
                                'src'   => $item->image,
                                'alt'   => 'official image of ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <div class="parliament-committee-fields">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
                    <?php echo $item->event->beforeDisplayContent; ?>
                </div>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_POSITION_LABEL'); ?></strong><br>
                    <?php echo $item->con_position; ?><br>
                <?php endif; ?>
                <?php if ($this->params->get('show_suburb_headings')) : ?>
                    <?php $location = []; ?>
                    <?php if (!empty($item->address)) : ?>
                        <?php $location[] = $item->address; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->suburb)) : ?>
                        <?php $location[] = $item->suburb; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->state)) : ?>
                        <?php $location[] = $item->state; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->postcode)) : ?>
                        <?php $location[] = $item->postcode; ?>
                    <?php endif; ?>
                        <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_ADDRESS_LABEL'); ?></strong><br>
                    <?php echo implode("<br>\n", $location); ?><br>
                <?php endif; ?>
                <?php if (!empty($item->misc)) : ?>
                    <?php echo $item->misc; ?>
                <?php endif; ?>
            </div>
        </div>
    <?php endforeach; ?>
</div>
```

## Estilização

As classes de estilo do Bootstrap podem ser definidas no arquivo `mydefault_myitems.php`.
Por exemplo, `<span class="fs-2">...</span>` é usado para aumentar o tamanho da fonte
do nome do contato. Outros estilos podem ser adicionados no arquivo `user.css`, por
exemplo, a personalização de listas com marcadores que aparecem apenas dentro de uma tag
que tenha a classe `contactList`.

Aqui estão os estilos inseridos no arquivo user.css para obter o layout
do Comitê Empresarial ilustrado acima.

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
.cat-list-row0 {
  background-color: #efefef;
}
.cat-list-row0:hover, .cat-list-row1:hover  {
  background-color: #ddd;
}
div.parliament-committee-fields {
  text-align: left;
  margin-top: 1rem;
}
div.parliament-committee-fields ul.fields-container {
  list-style-type: none;
  padding-left: 0;
}
div.parliament-committee-fields ul.fields-container span.field-label {
  font-weight: 700;
}
```

*Traduzido por openai.com*