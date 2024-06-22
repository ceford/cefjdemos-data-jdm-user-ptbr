<!-- Filename: Content_editors / Display title: Editores de conteúdo -->

Os editores padrões disponíveis no
<img src="https://docs.joomla.org/images/7/7b/Compat_icon_CMS.png"
decoding="async" data-file-width="87" data-file-height="17" width="87"
height="17" alt="Joomla multi" />

## Editor TinyMCE

O **TinyMCE** é o editor padrão para usuários do frontend e do backend.
O TinyMCE é um editor **WYSIWYG** (o que você vê é o que você obtém) que
permite, aos usuários, uma interface de processamento de texto familiar
para usar ao editar artigos e outros conteúdos.

O TinyMCE pode ser configurado com 3 conjuntos diferentes de botões da
barra de ferramentas

- O **conjunto 2** é atribuído a "público".
- O **conjunto 1** é atribuído a "gerente" e "registrado".
- O **conjunto 0** é a barra de ferramentas mais estendida e, por
  padrão, é atribuída ao "administrador", ao "editor" e aos
  "superusuários".

<img
src="https://docs.joomla.org/images/thumb/f/fb/Help30-editor-tinymce-advanced-en.png/600px-Help30-editor-tinymce-advanced-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/f/fb/Help30-editor-tinymce-advanced-en.png 1.5x"
data-file-width="669" data-file-height="114" width="600" height="102"
alt="Help30-editor-tinymce-advanced-en.png" />

Aprenda sobre as barras de ferramentas, os botões do editor e a
acessibilidade do
TinyMCE.

## Espelho de código

O editor CodeMirror foi projetado para facilitar a inserção de código da
HTML em um artigo ou descrição. O CodeMirror suporta realce de sintaxe e
preenchimento automático, conforme mostrado nesta captura de tela.

<img
src="https://docs.joomla.org/images/thumb/e/e2/Help25-screenshot-editor-codemirror-example-en.png/320px-Help25-screenshot-editor-codemirror-example-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/e2/Help25-screenshot-editor-codemirror-example-en.png 1.5x"
data-file-width="326" data-file-height="165" width="320" height="162"
alt="Help25-screenshot-editor-codemirror-example-en.png" />

O CodeMirror oferece algumas das mesmas vantagens de usar sem editor,
mas torna um pouco mais fácil trabalhar com código da HTML bruto.

Para configurar as opções:  Plugin do editor
CodeMirror

## Sem editor

Se a opção "sem editor" estiver selecionada para um usuário, um editor
de texto simples será exibido. Isso permite que você insira HTML bruta e
não formatada. Você pode usar o botão "visualizar" da barra de
ferramentas para visualizar como a HTML será exibido.

Observe que a opção "sem editor" pode ser útil se você estiver digitando
em "boilerplate" ou HTML personalizada, por exemplo, para criar um link
do PayPal. O TinyMCE reformata e remove automaticamente algumas HTMLs
quando um arquivo é salvo. Isso pode fazer com que a HTML complexa não
funcione corretamente.

Se isso acontecer, você pode alterar temporariamente o editor para "sem
editor" e criar o conteúdo desejado. Observe que se você deseja editar
este conteúdo no futuro, deve ter o cuidado de alterar seu editor para
"sem editor". Caso contrário, se você abrir e salvar o conteúdo com o
TinyMCE, poderá perder sua HTML personalizada.
