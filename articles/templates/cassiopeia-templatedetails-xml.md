<!-- Filename: J4.x:Cassiopeia_templateDetails.xml / Display title: Cassiopeia templateDetails.xml  -->

## Localização e Propósito

Você pode ver um exemplo de um arquivo `templateDetails.xml` listado em **Sistema → Modelos de Site → Detalhes e Arquivos Cassiopeia**. Você também pode editá-lo lá se tiver bons motivos para isso. Caso contrário, deixe-o como está! Todo modelo possui um arquivo como este, e um modelo filho inicialmente consiste em uma estrutura de arquivos contendo apenas este arquivo.

O arquivo `templateDetails.xml` contém os dados que o Joomla! precisa para gerenciar e exibir o modelo. Isso inclui metadados usados para fornecer informações sobre o modelo, as localizações de pastas e arquivos, as posições dos módulos do modelo e as opções de configuração selecionáveis pelo usuário. O conteúdo do arquivo templateDetails.xml varia de modelo para modelo.

## Cassiopeia templateDetails.xml

Arquivos em formato xml têm uma estrutura bem definida. Um arquivo xml deve ter a sintaxe correta ou não funcionará!

### Formato XML

A primeira linha de todo `templateDetails.xml` deve começar com a definição de doctype XML.

A próxima linha informa ao Joomla! que os dados neste arquivo são para uma extensão de template de site. Todos os dados do template estão contidos dentro das tags de abertura e fechamento.

```xml
<extension type="template" client="site">
...
</extension>
```

### Metadados

A primeira seção dos dados do template geralmente define informações sobre o template, por exemplo: nomes, datas, informações de contato, direitos autorais, número da versão e descrição.

```xml
<extension version="3.1" type="template" client="site">
  <name>cassiopeia</name>
  <version>1.0</version>
  <creationDate>2017-02</creationDate>
  <author>Joomla! Project</author>
  <authorEmail>admin@joomla.org</authorEmail>
  <copyright>(C) 2017 Open Source Matters, Inc.</copyright>
  <description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
  <inheritable>1</inheritable>
```

Note que um template que pode ter templates filhos tem o valor de "ineritable" definido como 1. Templates filhos têm este valor definido como 0. Esses dados são usados na listagem Templates: Templates (Site), como mostrado abaixo.

![lista de templates do site](../../../en/images/templates/templates-list.png)

A descrição contém uma chave de idioma e não a string de texto real da descrição. A chave é substituída pelo texto obtido de um arquivo de idioma em tempo de execução. Os arquivos de idioma são definidos na seção de idioma do `templateDetails.xml`.

![formulário de edição de estilo de templates](../../../en/images/templates/templates-edit-style.png)

### Pastas e Arquivos

Pastas e arquivos para o template Cassiopeia são armazenados em dois locais separados. Os arquivos php e relacionados são armazenados na pasta site/templates. Os arquivos de mídia (css, imagens, js e scss) são armazenados na pasta site/media. Esses locais são definidos no arquivo xml como segue:

```xml
  <files>
    <filename>component.php</filename>
    <filename>error.php</filename>
    <filename>index.php</filename>
    <filename>joomla.asset.json</filename>
    <filename>offline.php</filename>
    <filename>templateDetails.xml</filename>
    <folder>html</folder>
  </files>
  <media destination="templates/site/cassiopeia" folder="media">
    <folder>js</folder>
    <folder>css</folder>
    <folder>scss</folder>
    <folder>images</folder>
  </media>
```

Este é o padrão visto em todos os templates Joomla 4 e 5 modernos. A estrutura pode ser vista no formulário Templates: Customise (Cassiopeia):

![personalização da página do template cassiopeia](../../../en/images/templates/templates-customise-cassiopeia.png)

### Posições de Módulos

As posições de módulos disponíveis são definidas da seguinte forma:

```xml
  <positions>
    <position>topbar</position>
    <position>below-top</position>
    <position>menu</position>
    <position>search</position>
    <position>banner</position>
    <position>top-a</position>
    <position>top-b</position>
    <position>main-top</position>
    <position>main-bottom</position>
    <position>breadcrumbs</position>
    <position>sidebar-left</position>
    <position>sidebar-right</position>
    <position>bottom-a</position>
    <position>bottom-b</position>
    <position>footer</position>
    <position>debug</position>
  </positions>
```

Cada tag cria uma posição de módulo que está disponível na lista de posições em um formulário de edição de módulo. O formato simples da lista de posições significa que pode ser facilmente personalizado. Por exemplo, para adicionar uma nova posição de módulo à lista **em um template filho**, basta adicionar uma nova tag dentro da tag com um nome exclusivo usando todas as letras minúsculas sem espaços. Lembre-se de que isso apenas adiciona a posição aos formulários de edição de módulo, sendo necessário desenvolvimento adicional em outros arquivos de template para renderizar a nova posição na interface.

Cassiopeia tem posições de template suficientes! Se você acha que precisa de uma extra, provavelmente está errado. Lembre-se de que qualquer número de módulos pode ser atribuído a uma única posição e ordenados na página de lista de Módulos. Posições disponíveis:

![diagrama de posições do template Cassiopeia](../../../en/images/templates/cassiopeia-template-positions.png)

Você também pode ver as posições dos módulos em qualquer template: de **Sistema → Templates de Site** selecione o botão Opções na Barra de Ferramentas. No formulário de Opções, defina o campo de visualização de Posições de Módulo para Habilitado. Salve e Feche. Vá para o seu site e adicione ?tp=1 ao final de qualquer url (ou &tp=1 se já houver um ? na url). O Joomla exibirá todas as posições de template disponíveis, mesmo aquelas que não foram usadas:

![posições de templates Cassiopeia](../../../en/images/templates/templates-template-positions-by-tp.png)

### Idiomas

Arquivos de idioma permitem a tradução de texto estático no template. O arquivo tpl_cassiopeia.ini contém chaves para traduções de texto que serão vistas pelo Usuário. O arquivo tpl_cassiopeia.sys.ini contém chaves para traduções de texto que serão vistas pelo Administrador.

```xml
  <languages folder="language">
    <language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
    <language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
  </languages>
```

Os arquivos de idioma para o idioma padrão Inglês GB são armazenados em site/language/en-GB/. Outros idiomas seriam armazenados de forma semelhante em arquivos com o código de idioma ISO apropriado, por exemplo, fr-FR para Francês na França ou de-DE para Alemão na Alemanha (que pode ser diferente do Alemão Suíço e Alemão Austríaco).

### Opções

Um template pode oferecer opções de exibição que podem ser escolhidas pelo Administrador no formulário Template: Editar Estilo. Por exemplo, a aba Avançado do template Cassiopeia permite a um Administrador alterar a Marca, adicionar um Logotipo, selecionar um Esquema de Fontes e mais.

![formulário de edição de estilo de templates aba avançada](../../../en/images/templates/templates-edit-style-advanced.png)

As opções do template são definidas dentro de uma estrutura que cria campos dentro de conjuntos de campos (fieldsets). Cada conjunto de campos aparece como uma aba no formulário de edição. Esta é a estrutura que cria a aba Avançado vista acima.

```xml
  <config>
    <fields name="params">
      <fieldset name="advanced">
        <field
          name="brand"
          type="radio"
          label="TPL_CASSIOPEIA_BRAND_LABEL"
          default="1"
          layout="joomla.form.field.radio.switcher"
          filter="boolean"
          >
          <option value="0">JNO</option>
          <option value="1">JYES</option>
        </field>
        ...
      </fieldset>
    </fields>
  </config>
```

Opções individuais são definidas com a tag `<field>`. Cada `<fieldset>`, e cada parâmetro `<field>` dentro de um `<fieldset>`, requer um nome único definido por um atributo **name**. Este nome define o próprio parâmetro e é usado para passar configurações para os arquivos do front end. Cada parâmetro também contém um atributo **label** e um atributo **description**. O texto da etiqueta aparece com o parâmetro na tela de configurações para identificar para que o ajuste é usado, e informações mais detalhadas podem ser incluídas na descrição.

Um campo de parâmetro pode ser praticamente qualquer tipo de entrada de formulário com opções correspondentes. Isto é selecionado pelo atributo **type**. Quaisquer opções necessárias, como botões de rádio ou escolhas de seleção, são definidas nas tags `<option>`. Nomes de classes CSS podem ser definidos com o atributo **class** e um valor padrão pode ser definido usando o atributo **default**.

Abaixo estão as definições de opções no template padrão Cassiopeia. Neste exemplo, todos os Rótulos (Labels), Descrições e Opções estão usando definições de strings de idioma dos arquivos de idioma definidos na seção anterior, bem como algumas do núcleo do Joomla!, para que possam ser traduzidas para diferentes idiomas conforme necessário.

```xml
  <config>
    <fields name="params">
      <fieldset name="advanced">
        <field
          name="brand"
          type="radio"
          label="TPL_CASSIOPEIA_BRAND_LABEL"
          default="1"
          layout="joomla.form.field.radio.switcher"
          filter="boolean"
          >
          <option value="0">JNO</option>
          <option value="1">JYES</option>
        </field>

        <field
          name="logoFile"
          type="media"
          default=""
          label="TPL_CASSIOPEIA_LOGO_LABEL"
          showon="brand:1"
        />

        <field
          name="siteTitle"
          type="text"
          default=""
          label="TPL_CASSIOPEIA_TITLE"
          filter="string"
          showon="brand:1"
        />

        <field
          name="siteDescription"
          type="text"
          default=""
          label="TPL_CASSIOPEIA_TAGLINE_LABEL"
          description="TPL_CASSIOPEIA_TAGLINE_DESC"
          filter="string"
          showon="brand:1"
        />

        <field
          name="useFontScheme"
          type="groupedlist"
          label="TPL_CASSIOPEIA_FONT_LABEL"
          default="0"
          >
          <option value="0">JNONE</option>
          <group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
            <option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (local)</option>
          </group>
          <group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
            <option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
            <option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
          </group>
        </field>

        <field
          name="noteFontScheme"
          type="note"
          description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
          class="alert alert-warning"
        />

        <field
          name="colorName"
          type="filelist"
          label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
          default="colors_standard"
          fileFilter="^custom.+[^min]\\.css$"
          exclude="^colors.+"
          stripext="true"
          hide_none="true"
          hide_default="true"
          directory="media/templates/site/cassiopeia/css/global/"
          validate="options"
          >
          <option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
          <option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
        </field>

        <field
          name="fluidContainer"
          type="radio"
          layout="joomla.form.field.radio.switcher"
          default="0"
          label="TPL_CASSIOPEIA_FLUID_LABEL"
          >
          <option value="0">TPL_CASSIOPEIA_STATIC</option>
          <option value="1">TPL_CASSIOPEIA_FLUID</option>
        </field>

        <field
          name="stickyHeader"
          type="radio"
          label="TPL_CASSIOPEIA_STICKY_LABEL"
          layout="joomla.form.field.radio.switcher"
          default="0"
          filter="integer"
          >
          <option value="0">JNO</option>
          <option value="1">JYES</option>
        </field>

        <field
          name="backTop"
          type="radio"
          label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
          layout="joomla.form.field.radio.switcher"
          default="0"
          filter="integer"
          >
          <option value="0">JNO</option>
          <option value="1">JYES</option>
        </field>
      </fieldset>
    </fields>
  </config>
```

Neste exemplo, a tag `<fieldset name="advanced">` envolve todos os parâmetros e usa o atributo **name** para criar a aba *Avançado* na interface. Tudo o que é necessário para criar outra aba na interface é outra tag `<fieldset>` com um atributo **name** diferente. Com isso em mente, é relativamente simples criar tantas abas e parâmetros adicionais quanto necessário em um template.

Um uso potencial de parâmetros extras é em substituições ou layouts para templates pais ou filhos.

## Resumo

Este é o arquivo templateDetails.xml usado pelo Cassiopeia:

```xml
<?xml version="1.0" encoding="utf-8"?>
<extension type="template" client="site">
    <name>cassiopeia</name>
    <version>1.0</version>
    <creationDate>2017-02</creationDate>
    <author>Projeto Joomla!</author>
    <authorEmail>admin@joomla.org</authorEmail>
    <copyright>(C) 2017 Open Source Matters, Inc.</copyright>
    <description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
    <inheritable>1</inheritable>
    <files>
        <filename>component.php</filename>
        <filename>error.php</filename>
        <filename>index.php</filename>
        <filename>joomla.asset.json</filename>
        <filename>offline.php</filename>
        <filename>templateDetails.xml</filename>
        <folder>html</folder>
    </files>
    <media destination="templates/site/cassiopeia" folder="media">
        <folder>js</folder>
        <folder>css</folder>
        <folder>scss</folder>
        <folder>images</folder>
    </media>
    <positions>
        <position>topbar</position>
        <position>below-top</position>
        <position>menu</position>
        <position>search</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>main-top</position>
        <position>main-bottom</position>
        <position>breadcrumbs</position>
        <position>sidebar-left</position>
        <position>sidebar-right</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
    <languages folder="language">
        <language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
        <language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
    </languages>
    <config>
        <fields name="params">
            <fieldset name="advanced">
                <field
                    name="brand"
                    type="radio"
                    label="TPL_CASSIOPEIA_BRAND_LABEL"
                    default="1"
                    layout="joomla.form.field.radio.switcher"
                    filter="boolean"
                    >
                    <option value="0">NÃO</option>
                    <option value="1">SIM</option>
                </field>

                <field
                    name="logoFile"
                    type="media"
                    default=""
                    label="TPL_CASSIOPEIA_LOGO_LABEL"
                    showon="brand:1"
                />

                <field
                    name="siteTitle"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TITLE"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="siteDescription"
                    type="text"
                    default=""
                    label="TPL_CASSIOPEIA_TAGLINE_LABEL"
                    description="TPL_CASSIOPEIA_TAGLINE_DESC"
                    filter="string"
                    showon="brand:1"
                />

                <field
                    name="useFontScheme"
                    type="groupedlist"
                    label="TPL_CASSIOPEIA_FONT_LABEL"
                    default="0"
                    >
                    <option value="0">NENHUM</option>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
                        <option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (local)</option>
                    </group>
                    <group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
                        <option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
                        <option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
                    </group>
                </field>

                <field
                    name="noteFontScheme"
                    type="note"
                    description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
                    class="alert alert-warning"
                />

                <field
                    name="colorName"
                    type="filelist"
                    label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
                    default="colors_standard"
                    fileFilter="^custom.+[^min]\.css$"
                    exclude="^colors.+"
                    stripext="true"
                    hide_none="true"
                    hide_default="true"
                    directory="media/templates/site/cassiopeia/css/global/"
                    validate="options"
                    >
                    <option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
                    <option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
                </field>

                <field
                    name="fluidContainer"
                    type="radio"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    label="TPL_CASSIOPEIA_FLUID_LABEL"
                    >
                    <option value="0">TPL_CASSIOPEIA_STATIC</option>
                    <option value="1">TPL_CASSIOPEIA_FLUID</option>
                </field>

                <field
                    name="stickyHeader"
                    type="radio"
                    label="TPL_CASSIOPEIA_STICKY_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">NÃO</option>
                    <option value="1">SIM</option>
                </field>

                <field
                    name="backTop"
                    type="radio"
                    label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
                    layout="joomla.form.field.radio.switcher"
                    default="0"
                    filter="integer"
                    >
                    <option value="0">NÃO</option>
                    <option value="1">SIM</option>
                </field>
            </fieldset>
        </fields>
    </config>
</extension>
```

*Traduzido por openai.com*
