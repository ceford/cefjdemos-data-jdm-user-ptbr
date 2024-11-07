<!-- Filename: How_do_you_put_a_module_inside_an_article%3F / Display title: Módulos dentro de Artigos -->

## Introdução

Você geralmente vai querer associar módulos a artigos de alguma forma. Os módulos são normalmente alocados em posições de módulo, e essas posições aparecem em algum lugar na página da web conforme determinado pelo template. No entanto, às vezes é útil ter um módulo realmente incorporado dentro de um artigo. O Joomla possui um plugin chamado *Conteúdo - Carregar Módulos* para fazer isso. Quando ativado, um módulo pode ser incorporado em um artigo de três maneiras diferentes:

```
    {loadposition posição,[estilo]}
    {loadmodule tipo_mod, o título,[estilo]}
    {loadmoduleid idDoMódulo}
```

Onde `estilo` é um dos valores de Estilo de Módulo da aba Avançado do formulário de entrada de dados do módulo, por exemplo, html, contorno, tabela, cartão ou semCartão.  

## loadposition

Para inserir um módulo dentro de um artigo, você deve publicá-lo em uma posição e carregar essa posição no artigo da seguinte forma:

1. Crie um módulo e defina sua posição como ***minhaposicao***. ***minhaposicao*** pode ser qualquer valor que não entre em conflito com uma posição de template existente. No formulário de edição do módulo, digite a posição ***minhaposicao*** e pressione Enter em vez de selecioná-la na lista suspensa.
2. Atribua o módulo a **Todos** os Itens de Menu. Isso garantirá que ele sempre apareça, independentemente de como o visitante chegou ao artigo. O módulo não será exibido a menos que você use o comando para carregar o módulo em um artigo.
3. Edite o artigo e insira o texto ***{loadposition minhaposicao}*** no local onde deseja que o módulo apareça.

**Nota:** Se o plugin *Conteúdo - Carregar Módulos* estiver desativado, o texto *{loadposition minhaposicao}* aparecerá sem alterações no artigo. Além disso, o nome da posição deve estar todo em letras minúsculas. CapitalizaçãoMista falhará.  

## loadmodule

A sintaxe *{loadmodule yyy}* procura o primeiro módulo cujo **tipo** corresponda à string 'yyy'. Assim, você pode carregar um módulo *mod_login* colocando {loadmodule login} em seu texto. O tipo não é tão óbvio! Por exemplo, o Seletor de Idiomas tem o tipo **languages**. Para encontrar o tipo, você precisa procurar na lista de pastas de módulos com um gerenciador de arquivos/explorador e remover a parte *mod_* do nome da pasta.

Se você deseja carregar uma instância específica de um módulo, porque tem mais de um módulo de login, por exemplo, intitulado como Login 1, Login 2, etc., você deve usar {loadmodule mod_modType, modTitle} onde **mod_modType** seria mod_login e **modTitle** seria o nome/título dado à sua instância desse módulo. Então, no exemplo acima, você acabaria com **{loadmodule mod_login Login 2}**.

Você também pode adicionar o estilo que é usado para renderizar o módulo. Para fazer isso, adicione o estilo como terceiro parâmetro, como {loadmodule login,Login 2,xhtml}. Se você não adicionar um estilo, nenhum será usado.

## loadmoduleid

A sintaxe *{loadmoduleid z}* procura o módulo cujo `id` corresponde ao número `z`. Portanto, você poderia carregar o módulo com id 200 inserindo *{loadmoduleid 200}* em seu texto. Esta variante não utiliza parâmetros adicionais como o parâmetro `style`.

## Botão do Editor

Se o plugin editor-xtd *Botão - Módulo* estiver ativado, você pode usar o botão do editor *Módulo* para inserir as tags descritas acima de forma mais fácil no texto do editor. A lista de Módulos possui um botão na coluna Título para inserir por ID e um botão na coluna Posição para inserir por posição.

## Módulos dentro de Módulos

É possível incluir um módulo dentro de um módulo de *HTML Personalizado*. Eles são processados por plugins de conteúdo da mesma forma que os artigos.

Pode haver problemas de formatação, pois o estilo do módulo de *HTML Personalizado* envolverá o estilo do módulo incluído. É por isso que o botão do editor de *Módulo* não está disponível em módulos do tipo *Personalizado*.

*Traduzido por openai.com*  

