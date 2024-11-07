<!-- Filename: J4.x:Media:_Options / Display title: Mídia: Opções   -->

## Introdução

A página *Mídia: Opções* é usada para controlar o upload e armazenamento de mídia, tanto imagens quanto arquivos. **Atenção:** existem implicações de segurança associadas a alguns tipos de arquivo - é um caminho para invasão por hackers.

Para acessar o formulário *Mídia: Opções*, selecione o botão **Opções** na barra de ferramentas na página de Mídia. Os campos são bem comentados e fornecidos com valores padrão que devem ser adequados para quase todos os sites. Normalmente, você só precisa usar o formulário de opções se desejar manter Arquivos separados de Imagens ou se tiver um formato de arquivo incomum não incluído na lista padrão.

## Captura de Tela

![O formulário de Opções de Mídia](../../../en/images/media/media-options.png)

## Caminho para Arquivos e Pastas

Estes são itens separados no formulário de configuração, mas ambos apontam para a
pasta *images* em uma nova instalação do Joomla. Se você quiser armazenar
mídias não-imagem separadamente (por exemplo, PDFs, planilhas e arquivos de texto),
siga os seguintes passos:

1. Crie uma pasta chamada *files* na raiz da sua instalação do Joomla.
2. Habilite o plugin *FileSystem - Local* e configure-o, conforme descrito no
   artigo sobre [Locais de Arquivos de Mídia](jdocmanual?article=user/media/media-file-locations).
3. Insira o nome da pasta, *files*, no campo *Caminho para Pasta de Arquivos* do
   Formulário de Opções de Mídia.

No formulário de Opções, insira o nome da pasta no campo **Caminho para Pasta de Arquivos**. Certifique-se de não usar o nome de uma pasta principal já existente do Joomla.

Uma vez configurado, você poderá escolher entre as pastas de imagens e arquivos
na parte Local da visualização de Mídia.

![A página de mídia](../../../en/images/media/media-sample-data-cassiopeia.png)

## Tipos Adicionais de Imagem ou Documento

Você pode perceber que uma Imagem ou Documento não pode ser carregado. Se for o caso, verifique se
sua extensão está entre as *Extensões Permitidas*, se sua extensão está entre
os *Tipos de Extensões Legais* para a mídia e se está entre os 
*Tipos de MIME Legais* (você pode ter que procurar isso). Todos os três devem estar corretos
ou o upload será negado.
*Traduzido por openai.com*

