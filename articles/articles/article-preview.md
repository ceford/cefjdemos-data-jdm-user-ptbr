<!-- Filename: J4.x:Article_Preview / Display title: Artigo: Prévia  -->

## Introdução

Pode ser útil visualizar um artigo antes de publicá-lo. Existe um botão de *Visualização* na Barra de Ferramentas do formulário de *Edição de Artigo* no backend para esse propósito. No entanto, esse recurso utiliza o artigo salvo e não o conteúdo do formulário do editor. A funcionalidade de Visualização não está disponível no formulário de edição de artigo no frontend.

Você pode não querer tornar um artigo visível até que esteja concluído. Para isso, são necessárias estratégias diferentes para editores de frontend e backend.

## Pré-visualização do Frontend

A única maneira de manter um artigo semi-privado no front-end é definir seu Acesso como *Registrado* para que apenas usuários logados possam vê-lo.

- Faça login no frontend do site.
- Selecione o link *Editar* de um artigo para ser atualizado. Ou...
- Selecione o botão *Novo Artigo* abaixo dos layouts do blog.
  - Defina o nível de Acesso do artigo como *Registrado* até que esteja pronto para publicação.
  - Você pode adicionar um aviso de *Alerta* indicando que o artigo está em construção: `<div class="alert alert-warning">Em Construção</div>`.
- *Salvar & Fechar* para visualizar o artigo.

## Pré-visualização do Backend

Após o login na interface do Administrador:

- Selecione um artigo para editar ou crie e salve um novo.
- Para manter um novo artigo privado por enquanto, defina o Status como *Não Publicado* ou
  deixe como *Publicado* e ajuste a data de *Início da Publicação*.
- Faça alterações e *Salve* o artigo.
- Selecione o botão *Pré-visualização* na Barra de Ferramentas. Uma janela de Pré-visualização deve aparecer.
- Se você receber uma mensagem *A página solicitada não pode ser encontrada*, faça login no
  Frontend e tente novamente.
- Para fechar a janela de Pré-visualização, selecione o botão *X* no canto superior direito.

![A janela de pré-visualização](../../../en/images/getting-started/article-edit-preview.png)

*Traduzido por openai.com*

