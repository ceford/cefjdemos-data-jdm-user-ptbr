<!-- Filename: J3.x:Adding_custom_fields/Textarea_Field / Display title: Campo de Área de Texto -->

## Finalidade

O Campo de Área de Texto é uma área para entrada de texto em várias linhas. Um campo de texto simples não possui um Editor WYSIWYG.

### Opções

As opções especiais deste campo são:

- **Linhas** A altura da área de texto visível em linhas. Se omitido, a altura é determinada pelo navegador. O valor não limita o número de linhas que podem ser inseridas. As linhas estão ativas no backend enquanto se cria um artigo, um contato ou um componente de terceiros que suporta campos personalizados. Esta opção não tem impacto no tamanho do campo no frontend.
- **Colunas** A largura da área de texto visível em caracteres. Se omitido, a largura é determinada pelo navegador. O valor não limita o número de caracteres que podem ser inseridos. As colunas estão ativas no backend enquanto se cria um artigo, um contato ou um componente de terceiros que suporta campos personalizados. Esta opção não tem impacto no tamanho do campo no frontend.
- **Comprimento Máximo** O número máximo de caracteres que pode ser inserido.
- **Filtro** Permitir que o sistema salve certas tags HTML ou dados brutos.

![criação de campo de área de texto](../../../en/images/fields/fields-textarea-edit.png)

**Nota:** Neste exemplo, a inclusão do tipo de campo no Título é apenas para fins de demonstração. Deixe-o de fora dos seus próprios títulos de campo.

## Entrada de Dados

Simples: digite o texto para exibir.

![campo de entrada de dados em área de texto](../../../en/images/fields/fields-textarea-data-entry.png)

## Exibição de Dados

A captura de tela do site a seguir mostra o campo exibido em um artigo. A
opção *Exibição automática* é responsável pela posição do campo e
seu template é responsável pelo design do campo.

![exibição de campo de área de texto no site](../../../en/images/fields/fields-textarea-site.png)

O rótulo do campo começa um único bloco de texto, a menos que você tenha inserido tags HTML como `<p>...</p>`.

