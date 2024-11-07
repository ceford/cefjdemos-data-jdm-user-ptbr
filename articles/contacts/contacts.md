<!-- Filename: contacts.md / Display title: Contatos  -->

## Introdução

Um contato é uma coleção de informações pessoais sobre um indivíduo. Você pode querer tornar essas informações disponíveis em seu site para exibição pública ou privada. Por exemplo, você pode querer listar membros-chave da sua organização ou comunidade. O componente de Contato do Joomla! é projetado para esse propósito. Ele permite que você liste pessoas e suas informações pessoais no seu site, não necessariamente usuários registrados. Você também pode permitir que qualquer pessoa, ou apenas usuários registrados, enviem e-mails para essas pessoas.

Como exemplo do uso de dados pessoais, você pode olhar a página da WikiPedia sobre os comitês parlamentares do Reino Unido. Lá, você verá listas de comitês com informações pop-up em cada presidente individual. Se você seguir um link para qualquer comitê, verá uma lista de membros com informações selecionadas sobre cada indivíduo. Para fazer algo assim no Joomla, você configuraria categorias e subcategorias para cada comitê. Assim:

```
Câmara dos Comuns
- Negócios
- Cultura
- ...
Câmara dos Lordes
- Comunicações
- Constituição
- ...
```
Cada membro do comitê possui informações adicionais que não estão presentes nos dados padrão - afiliação política, como Conservador, Trabalhista ou SNP, e circunscrição, a área do país que representam. Esses itens podem ser coletados usando Campos Personalizados.

É necessário cuidado na coleta e exibição de informações pessoais. Os indivíduos podem ser muito sensíveis a ter qualquer informação disponibilizada online.

## Dados de Contato

Os contatos são criados por meio da página de lista de Contatos. Selecione o botão `Novo` na Barra de Ferramentas para adicionar uma nova entrada. Existe também um plugin **Usuário - Criador de Contato** que cria automaticamente um contato quando um novo usuário é registrado.

No formulário **Contatos: Edição**, insira todos os dados que você tiver disponíveis sobre o contato.

![captura de tela de entrada de dados](../../../en/images/contacts/contact-data-entry.png "Captura de Tela da Entrada de Dados")

**Notas:**

Na captura de tela, a **Posição** foi inserida como *Presidente*, o que fazia sentido no contexto de uma lista de categoria de membros do comitê, mas não faz sentido no contexto de uma lista de Contatos em Destaque que consiste em todos os Presidentes de todos os Comitês. Isso precisa ser mais específico: *Presidente do Comitê de Cultura, Mídia e Esporte*.

Os campos **Primeiro...**, **Segundo...** e **Terceiro Campo de Ordenação** precisam de palavras adicionadas a cada entrada para permitir a classificação por uma ordem definida pelo usuário, como uma ordem convencional de sobrenome e nome. Isso é abordado mais adiante neste artigo.

A guia **Informações Diversas** contém um campo de edição de texto com uma breve declaração pessoal.

A guia **Extra** contém os campos personalizados *Partido* e *Circunscrição*.

A guia **Formulário** contém configurações para o formulário de contato por e-mail. Se um endereço de e-mail não for inserido, este campo não é exibido.

## Exibição de Contato

O componente de Contato fornece quatro itens de menu para exibir dados de contato:

* Contato Único
* Contatos em Destaque
* Listar Contatos em uma Categoria
* Listar Todos os Contatos em uma Árvore de Categorias

É uma boa ideia experimentar cada tipo de menu para ver como é o resultado.
Alguns exemplos:

### Listar Todas as Categorias em uma Árvore de Categorias de Contatos

Neste caso, a árvore de categorias consiste em uma categoria pai e duas subcategorias:
```
Câmara dos Comuns
- Comitê de Negócios
- Comitê de Cultura
```
![todas as categorias em uma árvore de categorias](../../../en/images/contacts/contact-all-committees.png "Todas as Categorias em uma Árvore de Categorias de Contatos")

A segunda linha de cada entrada vem da Descrição da Categoria.

Se você selecionar um dos links do Comitê, a página do Comitê poderá ser assim:

![contatos em uma categoria](../../../en/images/contacts/contact-culture-committee.png "Contatos em uma Categoria")

O layout não está exatamente como desejado. Seria bom incluir uma
imagem em miniatura de cada indivíduo e um layout melhor dos detalhes. Isso
pode ser feito com uma substituição de template (mais tarde).

### Listar Contatos em uma Categoria

Para o Comitê de Negócios, há um item de menu Listar Contatos em uma Categoria.
Isso faz com que um layout diferente seja usado:

![lista de categoria de contatos](../../../en/images/contacts/contact-category-list.png "Lista de Categoria de Contatos")

Melhor, mas ainda não está certo! Foi necessário substituir o estilo
da imagem. Novamente, parece que uma substituição de template poderia ser útil.

### Contatos em Destaque

Neste exemplo, os Presidentes de todos os comitês foram marcados como destaque.

![contatos em destaque](../../../en/images/contacts/contact-featured.png "Contatos em Destaque")

## Ordem de Classificação

A ordem na qual os contatos aparecem pode ser definida nas opções do componente de Contato ou em um item de menu. A última configuração substitui a primeira, se estiver definida. As configurações disponíveis são as seguintes:
* **Nome** O nome do contato. Isso pode não ser adequado para ordenação alfabética.
* **Nome de Classificação** Estes são os três campos de *Campo de Classificação* no formulário de dados do Contato mencionado anteriormente.
* **Ordenação** Esta é a ordem em que os contatos aparecem na lista de Contatos.
* **Ordenação de Contatos em Destaque** Contatos em destaque aparecem antes de outros contatos, mas fora isso, os contatos são exibidos na ordem da lista.

*Traduzido por openai.com*

