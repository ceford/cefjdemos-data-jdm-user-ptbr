<!-- Filename: J6.x:Media_File_Locations / Display title: Locais de Arquivos de Mídia -->

## Introdução

Por padrão, o Joomla armazena tanto as imagens dos usuários quanto os arquivos de documentos na pasta */images* da instalação do Joomla. Quaisquer links para essa mídia não são processados diretamente pelo Joomla. O servidor web os envia quando solicitado pelo navegador.

Se você tiver muitos documentos, pode querer mantê-los em uma pasta separada, mais especificamente uma pasta */files* também na raiz do site Joomla.

Para configurar um local para arquivos separado das imagens, primeiro crie uma nova pasta na raiz de sua instalação, por exemplo, **files**. Lembre-se, ela fará parte de um link de URL, então use letras minúsculas e evite espaços ou pontuações.

### Plugin FileSystem - Local

Encontre o plugin *FileSystem - Local* na lista de plugins e abra-o. Adicione a nova pasta *files* à lista de locais onde você pode manter a mídia. Basta clicar no botão + e selecionar **files** da lista de pastas disponíveis.

![Plugin do Sistema de Arquivos](../../../en/images/plugins/plugin-group-file-system-local.png)

A opção **Criar Miniaturas** configurada em **Sim** causa a criação de pequenas imagens com uma altura ou largura máxima de 200 pixels em media/cache/com_media/thumbs com a mesma estrutura de pastas que a pasta de mídia. Isso deve aumentar significativamente a velocidade de exibição de uma pasta com muitas imagens. Não é necessário para arquivos, pois eles são representados por ícones.

Certifique-se de que o plugin esteja ativado. **Salvar & Fechar**.

*Traduzido por openai.com*

