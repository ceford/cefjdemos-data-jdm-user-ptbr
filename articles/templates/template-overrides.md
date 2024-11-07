<!-- Filename: J4.x:Template_Overrides / Display title: Substituições de Modelo  -->

## Introdução

As extensões do Joomla definem a aparência de sua saída com arquivos de modelo, que contêm marcação HTML e PHP gerada por HTML, e arquivos CSS que definem layout, esquema de cores, fontes e assim por diante. Isso pode ser perfeitamente adequado às suas necessidades, especialmente porque você pode alterar a aparência com seus próprios estilos CSS. Às vezes, você quer mostrar informações adicionais ou talvez menos informações. Para isso, você precisa criar um substituto de modelo.

Muitas das extensões do Joomla têm modelos de saída bastante complexos que são difíceis de ler. Você precisa ter um bom entendimento de HTML, PHP e CSS para enfrentá-los. Portanto, este artigo ilustra o processo de criação de um substituto para o formulário de logout que está, na verdade, no módulo de login, mod_login. O proprietário do site gostaria que o formulário de logout mostrasse o horário em que o logout automático ocorrerá após um período de inatividade.

## Exemplo: Sobrescrita de Template para mod_login

Comece selecionando **Sistema → Templates → Templates do Site** no menu do Administrador e, em seguida, selecione o item Detalhes e Arquivos do Cassiopeia. Isso abrirá o formulário Templates: Personalizar (Cassiopeia):

![customizar template aba do site cassiopeia](../../../en/images/templates/templates-customise-cassiopeia.png)

**Importante:** não edite nenhum dos arquivos fornecidos como parte do template Cassiopeia. Na próxima atualização do Joomla, esses arquivos podem ser sobrescritos e suas edições serão perdidas.

A pasta html é onde estão localizadas as sobrescritas. Se você expandir a pasta html, verá que já existem sobrescritas para layouts, mod_custom, mod_menu e tinymce. Expanda cada um para ver o que há neles. Não há mod_login neste estágio.

## Criar Substituições

Selecione a aba Criar Substituições para ver a lista de Módulos, Componentes, Plugins e Layouts para os quais você pode criar substituições:

![modelos personalizar aba de substituições cassiopeia](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Selecione o item mod_login. Os arquivos PHP do template mod_login serão copiados para a pasta html, e você será retornado à aba Editor. Expanda as pastas html e mod_login. Você verá os arquivos default.php e default_logout.php.

Você não quer o arquivo default.php, pois é uma substituição para o formulário de login. Selecione-o e depois clique no botão **Excluir Arquivo** na Barra de Ferramentas. No diálogo de alerta, confirme que você deseja excluir o arquivo.

Note como é fácil excluir arquivos se você mudar de ideia. E com o botão Gerenciar Pastas, você também pode excluir pastas inteiras. Tenha cuidado para não excluir algo que você não criou.  

## Editar default_logout.php

Na aba Editor, selecione o arquivo default_logout.php. Observe os botões no canto superior direito: Mostrar Arquivo Original e Mostrar Diferenças. O último foi definido como Sim para a captura de tela a seguir, a fim de mostrar algumas linhas de código adicionadas próximo ao topo do arquivo. Essas linhas de código calculam quando a sessão do usuário irá expirar após o carregamento da página que contém o formulário de logout.

![personalizar modelos aba overrides cassiopeia](../../../en/images/templates/cassiopeia-customisation-edit-logout-override.png)

A área de Dif mostra linhas adicionadas em um fundo verde e linhas deletadas em um fundo vermelho. Não há linhas deletadas neste caso. O código é mostrado aqui caso deseje copiá-lo para tentar isso você mesmo.

```php
    use Joomla\CMS\Factory;

    date_default_timezone_set('Europe/London');
    $config = Factory::getContainer()->get('config');
    $lifetime = $config->get('lifetime', 0);
    $time = time() + $lifetime * 60;
    $endTime = date('H:i:s', $time); // time() já retorna um tempo em segundos
```

Mais adiante no arquivo de override, linha 36, algumas outras linhas foram adicionadas para mostrar a mensagem desejada:

```html
<p class="text-center">
Sua sessão irá expirar às <br><?php echo $endTime; ?>
</p>
```

Salve e recarregue a página do site que contém o formulário de logout.

![personalizar modelos aba overrides cassiopeia](../../../en/images/templates/cassiopeia-customisation-logout-override-result.png)

Você deverá ver o formulário de logout mudar cada vez que a página for recarregada. Mas e se mudar de ideia? Ou tiver diferentes opções para diferentes grupos de Usuários? Bem-vindo aos Layouts, o assunto de um artigo separado.

## Outros Substituições

A aba Criar Substituições do formulário Templates: Personalizar (Cassiopeia) é usada para criar qualquer um dos elementos de saída do Joomla para os quais é possível criar substituições. Os nomes das pastas de substituição geralmente começam com com\_, mod\_ ou plg\_. Note que a segunda parte de uma pasta de substituição de plugin indica o grupo do plugin. Aqui está uma seleção de exemplos de pastas de substituição:

![aba de substituições personalizar templates cassiopeia](../../../en/images/templates/templates-customise-example-override-folder.png)

## Substituições de Layout

Pequenos arquivos de layout são frequentemente usados para elementos individuais de páginas do Joomla! O botão Leia Mais dos artigos, a imagem de introdução e a imagem completa são todos exemplos de elementos gerados por seus próprios arquivos de layout. Esses micro-layouts estão localizados na pasta /layouts. Por exemplo, na visualização do Blog da Categoria, o arquivo blog_item.php contém o código para posicionar o título do artigo, uma imagem de introdução, o texto de introdução, assim como várias outras partes relevantes da página. Ele faz isso usando uma chamada LayoutHelper, passando o layout a ser usado como parâmetro. Aqui está um exemplo, a chamada para inserir o Título do Artigo no layout do blog:

```php
<?php echo LayoutHelper::render('joomla.content.blog_style_default_item_title', $this->item); ?>
```

A localização do arquivo para este elemento específico é encontrada substituindo os pontos (.) por barras (/) e adicionando /layouts/ no início e .php no final:

```php
    JOOMLAROOT/layouts/joomla/content/blog_style_default_item_title.php
```

Quando um arquivo de substituição é criado, ele é encontrado em:

```php
    JOOMLAROOT/templates/cassiopeia/html/layouts/joomla/content/blog_style_default_item_title.php
```

## Informações Adicionais

- Noções Básicas de Template
- Pastas e Arquivos do Template Cassiopeia
- Personalização do Template Cassiopeia
- Substituições de Template
- Layouts de Template
- Template Cassiopeia Simplificado - Um Estudo de Caso - um template simples 
  baseado no Cassiopeia

*Traduzido por openai.com*

