<!-- Filename: How_do_you_put_a_module_inside_an_article%3F / Display title: Como você coloca um módulo dentro de um artigo? -->

Joomla!  <span class="small">≥ </span>2.5 series

Você geralmente desejará associar módulos a artigos de alguma forma. Os
módulos são alocados nas posições de módulos e as posições de módulos
aparecem em algum lugar na página web conforme determinado pelo tema. No
entanto, às vezes é útil ter um módulo realmente incorporado no artigo.
O núcleo do Joomla! oferece três maneiras de fazer isso: loadposition,
loadmodule e loadmoduleid. O plugin "Conteúdo - Carregar módulos" deve
estar habilitado.

Sintaxe:

- {loadposition position,\[style\]}
- {loadmodule mod_type,the title,\[style\]}
- {loadmoduleid moduleId}

## loadposition

Para inserir um módulo dentro de um artigo, você publica o módulo em uma
posição e carrega essa posição no artigo da seguinte forma:

1.  Crie um módulo e defina sua posição para ***minhaposição***.
    ***minhaposição*** pode ser qualquer valor que não entre em conflito
    com uma posição do tema existente. Digite a posição
    ***minhaposição*** e pressione enter em vez de selecioná-la na lista
    suspensa.
2.  Atribua o módulo a **todos** os itens de menus. Isso garantirá que
    ele sempre apareça, não importa como o visitante chegou ao artigo. O
    módulo não será exibido a menos que você coloque o comando para
    carregar o módulo em um
    artigo.
3.  Edite os artigos onde deseja que este módulo apareça e insira o
    texto ***{loadposition minhaposição}*** no artigo, no local onde
    deseja o módulo.

\*Observe que isso só funcionará se o  plugin *Conteúdo - Carregar
módulo*
(apenas em inglês) estiver habilitado. Se este plugin estiver
desabilitado, o texto *{loadposition minhaposição}* será exibido
inalterado no artigo. Além disso, o nome da posição deve ser todo em
minúsculas. A "CapitalizaçãoCamelo" falhará.

## loadmodule

Uma alternativa para "{loadposition xx}" é a variação "{loadmodule yyy}"
que é tratada pelo mesmo plugin.

Neste caso, o plugin procura o primeiro módulo cujo **tipo** corresponde
à string "yyy". Então você pode carregar um módulo "mod_login" colocando
{loadmodule login} em seu texto. Se você deseja carregar uma instância
específica de um módulo, talvez pelo fato de você tem mais de um módulo
de início de sessão (por exemplo, intitulado como "Login 1", "Login 2",
etc.), terá que usar {loadmodule mod_tipodomódulo, títulodomódulo} onde
mod\_**tipodomódulo** seria "mod_login" e **títulodomódulo** seria o
nome/título dado à sua instância desse módulo. Então, no exemplo acima,
você teria **{loadmodule mod_login Login 2}**. Você também pode
adicionar o estilo usado para renderizar o módulo. Para fazer isso,
adicione o estilo como o terceiro parâmetro (como, por exemplo,
{loadmodule login,login2,xhtml}). Se você não adicionar um estilo,
"nenhum" será usado.

## loadmoduleid

Desde a versão 3.9.0 do Joomla!, uma alternativa para
`{loadposition xx}` e `{loadmodule yyy}` é a variação `{loadmoduleid z}`
que é tratada pelo mesmo plugin.

Neste caso, o plugin procura o módulo cujo `id` corresponde ao número
`z`. Então você pode carregar o módulo com id 200 colocando
`{loadmoduleid 200}` em seu texto. Esta variante não "entende"
parâmetros adicionais como o parâmetro `style`.

## Botão do editor (desde a versão 3.5 do Joomla!)

Se o "Botão - Módulo" do plugin do editor-xtd estiver ativado, você
poderá usar o botão "Módulo" do editor para inserir as tags descritas
acima mais facilmente no texto do editor. Desde a versão 3.9 do Joomla!
também está disponível a variante `loadmouleid`.

## Módulos dentro de módulos

É possível, nas versões 2.5+ e 3.x+ do Joomla!, incluir um módulo dentro
de um módulo de "HTML personalizada". Eles são processados por plugins
de conteúdo da mesma forma que os artigos.

Para que isso funcione, a opção **Preparar conteúdo** deve estar
habilitada conforme mostrado nesta captura de tela.

<img
src="https://docs.joomla.org/images/d/de/J3x_custom_html_prepare_content_option-en.png"
decoding="async" data-file-width="633" data-file-height="298"
width="633" height="298"
alt="Mostrando a opção &quot;Preparar conteúdo&quot; em um módulo de &quot;HTML personalizada&quot;." />

Ao fazer isso, você deve se lembrar que pode ter problemas de
formatação, pois o "cromo" do módulo de "HTML personalizada" envolverá o
"cromo" do módulo incluído, possibilitando causar efeitos indesejáveis
de formatação ou disposição (layout). É por isso que o botão "Módulo" do
editor não está disponível em módulos dos tipos "Personalizados".
