<!-- Filename: Adding_an_image_to_an_article / Display title: Adicionando uma imagem em um artigo -->

## Introduction

How best to add images to an article depends on which version of Joomla
and which editor are in use. This article has illustrations for Joomla
4, with notes on differences in Joomla 3, and TinyMCE the Joomla default
editor. To get started, open an article for editing:

- **Select** **Content **→** Articles** in the Administrator menu.
- **Select** the title of the article you wish to edit

After inserting the article text, place the cursor at the location where
the image should appear.

## Adding a local image

If the image is located in the images folder of your Joomla installation
you should insert the image using the **CMS Content **→** Media** button
In the TinyMCE edit toolbar (In Joomla 3: Select the Image button):

<img
src="https://docs.joomla.org/images/5/5e/Adding-an-image-to-an-article-cms-content-media.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Adding an image" />

In the popup window, navigate to the image you want to use and click to
select it. On selection a form will appear prompting for additional
data. In Joomla 4 the form is to the left. In joomla 3 the form is at
the bottom (scroll down):

<img
src="https://docs.joomla.org/images/d/d4/Adding-an-image-to-an-article-selected-image.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Selecting an image" />

Defina as propriedades da imagem conforme necessário. Na maioria dos
casos você certamente deve preencher o campo de descrição da imagem
(texto alternativo). Os outros campos são usados para personalizar a
aparência da imagem com sua própria CSS.

- **Descrição da imagem**: Este se torna o atributo **alt**ernativo da
  imagem, um recurso importante para acessibilidade e conformidade com
  os padrões da web. No Joomla 3 é rotulado como **título da imagem**.
- **Classe da imagem**: Se uma imagem for usada sem legenda, algumas
  classes personalizadas podem ser aplicadas aqui. Por exemplo, no
  Joomla 4, **float-end ms-2 mb-1** alinhará a imagem à direita e
  flutuará o texto em torno dela com margens à esquerda e abaixo para
  evitar que o texto toque na imagem. No Joomla 3, o estilo equivalente
  é **pull-right**.
- **Classe da figura**: Se uma legenda for definida, uma classe de
  alinhamento, se houver, deve ser aplicada à figura. É uma marcação
  html que inclui a marcação img. Observe que no Cassiopeia as margens
  são aplicadas pela folha de estilo do modelo.
- **Legenda da figura**: Habilita a legenda que exibe o título da imagem
  abaixo da imagem.

**In Joomla 3**

- **Flutuação da imagem**: Define o alinhamento da imagem. Por padrão, o
  atributo de alinhamento é **não definido**.
- **Classe da legenda**: Aplica a classe inserida no elemento
  *figcaption*.

Selecione o botão para *inserir mídia* para inserir a imagem. A tela
para inserir imagem será fechada e a imagem será exibida no editor. Ou
selecione o botão para *cancelar* para sair da tela para inserir imagem.

**Dica:** selecione o botão para alternar editor para ver os estilos de
imagens e legendas aplicados.

### Using Drag and Drop for Local images

In both Joomla 4 and Joomla 3 you can drag an image from the desktop or
a file browser directly into the article text and the image will be
uploaded to the media folder and placed in the article. The only snag is
that all such uploaded images will be placed in the same media folder.
The location of the Images Directory used for upload and whether this
feature is enabled (On by default) are set in the TinyMCE configuration
Options.

## Adding a remote image

If the image you wish to use is not in the images folder of your Joomla
installation a slightly different procedure is needed.

- **Select** **Insert **→** Image** from the TinyMCE toolbar to open a
  dialog box. In Jooml 3, use the Image icon and the same dialog as used
  for local images.
- **Insert** the image url in the Source field.
- **Fill out** the other fields as required.
- **Advanced** provides some formatting options applied as in-line
  styles. Experiment with 1rem, 2, groove. (This feature is incomplete)

<img
src="https://docs.joomla.org/images/3/39/Adding-an-image-to-an-article-insert-edit-image.png"
class="thumbborder" decoding="async" data-file-width="480"
data-file-height="477" width="480" height="477"
alt="Data for a remote image" />

### Using Drag and Drop for Remote images

You can drag and drop an image from a remote web site directly into your
article text. But be aware that this may also copy the image container
html with class statements not valid for your site.

## Carregando imagens usando a tela para inserir imagem

Você pode carregar novas imagens usando a tela de mídia (a tela de
imagem no Joomla 3).

- Primeiro abra o navegador de mídia e navegue até a pasta onde você
  deseja armazenar as novas imagens para o artigo atual.
- Selecione o botão para carregar no canto superior esquerdo da tela de
  mídia (no Joomla 3, role para baixo até o botão para procurar na parte
  inferior do formulário de imagem) para abrir um navegador de arquivos.
- Selecione os arquivos de imagem que você deseja carregar. Selecione
  abrir, no navegador de arquivos, para confirmar a seleção. Observação:
  o estilo e o layout do navegador de arquivos dependem do navegador e
  do sistema operacional que você está usando. No Joomla 4 o
  carregamento é imediato. No Joomla 3, selecione o botão para iniciar
  carregamento.
- O(s) arquivo(s) selecionado(s) aparece(m) em ordem alfabética na tela
  de mídia/imagem.
- Quando o carregamento estiver concluído, um aviso de confirmação verde
  aparecerá na parte superior da tela.

Agora você pode selecionar e inserir a imagem carregada como antes.
