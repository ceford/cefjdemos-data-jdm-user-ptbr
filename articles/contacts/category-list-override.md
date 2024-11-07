<!-- Filename: category-list-override.md / Display title: Substituição da Lista de Categorias  -->

## O Item de Menu Listar Contatos em uma Categoria

Pode ser uma opinião pessoal, mas para mim, o layout padrão da lista de categorias de Contatos não é muito satisfatório. Meus problemas:

* As fotos dos contatos são muito grandes, com quase 500 pixels de largura.
* O nome do contato não é suficientemente destacado.
* A lista de detalhes pessoais em bullet não tem um cabeçalho e parece isolada.
* A Posição não tem um cabeçalho e pode parecer isolada.
* Os campos de endereço e código postal estão ausentes.
* Os dados de localização estão incompletos.
* A declaração pessoal está faltando.
* A lista está disposta em uma tabela que é um pouco melhor em telas estreitas, mas parece apertada.

Então, como consertar isso ao meu gosto?  

## Estilização

A imagem possui o estilo CSS `contact-thumbnail img-thumbnail`. As ferramentas de desenvolvedor do navegador indicam que img-thumbnail está configurado para `max-width: 100%;`, mas contact-thumbnail não é utilizado. A única ocorrência desse estilo em todo o site está nesta localização, então parece seguro definir uma substituição em user.css para restringir a largura da imagem. E o tamanho da fonte do nome do contato pode ser aumentado utilizando sua tag `a` envolvente:

```css
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
```

A lista com marcadores dos campos personalizados pode ser melhorada removendo os marcadores e o padding, selecionando apenas listas com marcadores que aparecem dentro de uma tag que tem uma classe de contactList:

```css
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
```

![styled business committee](../../../en/images/contacts/contact-business-committee-styled.png "Styled Business Committee")

Isso é o máximo que pode ser feito com estilização. Melhor, mas ainda não o suficiente. Para adicionar mais itens e alterar o layout será necessário uma substituição de layout.

## Substituição do Layout do Template

A pasta com_contact/tmpl/category contém três arquivos PHP: default.php, default_children.php e default_items.php. O último desta lista contém o layout da tabela para a lista.

Os arquivos de substituição são criados via Sistema / Templates do Site / Detalhes e Arquivos do Cassiopeia / Criar Substituições. Selecione com_contact e depois categoria. A pasta html então contém com_contact/category com os três arquivos de template mencionados acima. O arquivo default_items.php é o que deve ser selecionado para edição. As linhas 83 a 203 contêm a tabela usada para o layout.

Pode não ser óbvio, mas $this->items é um array de membros da categoria e cada membro realmente contém todos os dados de cada item, não apenas aqueles mencionados nas configurações do menu.

A seguir está uma substituição para a seção `<table>...</table>` do arquivo default_items.php usando um grid do Bootstrap. Em telas estreitas, as três colunas são empilhadas. Em telas com mais de 768 pixels, as colunas estão lado a lado. Mais explicações seguem o código.

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
                                'alt'   => 'imagem oficial de ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong>Posição</strong><br>
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
                        <strong>Endereço</strong><br>
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
### Explicação

A lista de contatos pode conter itens que não estão publicados ou têm datas publish_up e publish_down que não são atuais. Eles precisam ser excluídos da exibição e um contador separado é necessário para manter a alternância de cores de fundo em cada linha.

A tag img é renderizada como:
```
<img src="/j51/images/parliament/Official_portrait_of_Liam_Byrne_crop_2.jpg"
alt="imagem oficial de Liam Byrne" class="contact-thumbnail img-thumbnail"
width="479" height="639" loading="lazy">
```
A classe `<span class="fs-2">...</span>` define o nome do contato com tamanho de fonte 2, que seria o mesmo que Cabeçalho 2.

O item `show_suburb_headings` está sendo usado como proxy para mostrar o endereço completo, já que alguns dos itens de endereço individual não têm os seletores Mostrar/Ocultar no item de menu.

### Estilo Adicional

A versão em grade da lista de contatos precisa de estilos adicionais em user.css:
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
```

### Resultado

![comitê de negócios em grade](../../../en/images/contacts/contact-business-committee-grid.png "Comitê de Negócios em Grade")

*Traduzido por openai.com*

