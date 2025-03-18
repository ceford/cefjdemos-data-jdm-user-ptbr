<!-- Filename: J5.x:Add_a_class_selector_to_the_create_link_dialog / Display title: Artigo: Editar - Estilos de Link -->

## Descrição

As classes de link personalizadas adicionadas às opções do editor TinyMCE permitem que você transforme rapidamente um link de artigo em um botão ou adicione outros efeitos visuais sem precisar modificar o código HTML diretamente.

### Passos para Usar o Seletor de Classe

1. No Painel Inicial, vá para a lista de Plugins e encontre o plugin TinyMCE.
2. Abra o plugin TinyMCE e, com a aba Plugin selecionada, role até a parte inferior.
3. Adicione classes à *Lista de Classes de Links*. Por exemplo, classes do Bootstrap para criar botões elegantes. Você pode precisar rolar a lista da esquerda para a direita ou alterar a ampliação da tela para ver os botões de adicionar, remover e ordenar no final.
4. Salvar & Fechar.

![Set link classes in tinymce](../../../en/images/articles/article-edit-link-style-tinymce.png)

Você pode encontrar exemplos de modelos que usam Bootstrap nativamente na [Documentação Oficial do Bootstrap](https://getbootstrap.com/docs/5.3/components/buttons/).

Aqui estão algumas classes que você pode usar para variantes de botões do Bootstrap:

- `btn btn-primary` para um botão primário
- `btn btn-secondary` para um botão secundário
- `btn btn-success` para um botão de sucesso
- `btn btn-danger` para um botão de perigo
- `btn btn-warning` para um botão de aviso
- `btn btn-info` para um botão de informação
- `btn btn-light` para um botão claro
- `btn btn-dark` para um botão escuro
- `btn btn-link` para um botão de link

#### Alternativas ao Botão Contorno

Você também pode usar as variantes de botão de contorno:

- `btn btn-outline-primary` para um botão primário contornado
- `btn btn-outline-secondary` para um botão secundário contornado
- … (etc.)

#### Para tamanhos de botões, adicione estas classes

- `btn-lg` para um botão grande
- `btn-sm` para um botão pequeno

**Exemplo:** `btn btn-dark btn-lg` (um botão grande e escuro)

## Criar um link em um artigo

1. Abra um artigo e selecione um texto, uma palavra ou frase, para criar um link.
2. Selecione o ícone de Link que aparece ao selecionar algum texto.
3. Insira a URL para o link.
4. Na parte inferior do diálogo de criação de link, selecione uma das classes configuradas.
5. Salve o Link.
6. Salve o Artigo.
7. Visualize o Artigo.

![Apply link style in an article](../../../en/images/articles/article-edit-link-style-apply.png)

E este é um exemplo onde a classe Link Button foi definida como `btn btn-sm btn-outline-info` e o texto vinculado é *Bootstrap*:

![Preview of a custom Link Button](../../../en/images/articles/article-edit-link-style-preview.png)

## Uso Avançado: Aplicando Classes Personalizadas

Este recurso não se limita às classes do Bootstrap. Você também pode aplicar suas próprias classes CSS personalizadas para necessidades específicas. Por exemplo, você pode adicionar um ícone antes do link com um efeito de destaque. Isso facilita a estilização de links sem a necessidade de modificar o código-fonte do artigo.  
*Traduzido por openai.com*

