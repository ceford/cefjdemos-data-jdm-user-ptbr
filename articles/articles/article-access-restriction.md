<!-- Filename: J6.x:Article_Access_Restriction / Display title: Artigo: Restrição de Acesso   -->

## Introdução

Existem várias razões para restringir o acesso a artigos em um site. Alguns conteúdos podem ser privados para usuários específicos, como membros de um comitê. Ou o site pode conter conteúdo comercial pago. O Joomla oferece um poderoso sistema de Lista de Controle de Acesso (ACL) para restringir o acesso. Ele é descrito em um artigo separado sobre [Controle de Acesso](jdocmanual?article=user/users/access-control) na seção de Usuários deste manual.

Este artigo descreve a implementação de restrição de acesso no formulário *Artigo: Editar*. 

## Restrição por Nível de Acesso

O Joomla fornece os Níveis de Acesso vistos na captura de tela a seguir:

![Níveis de acesso do usuário](../../../en/images/articles/article-access-user-groups.png)

Os níveis de acesso aparecem na aba *Conteúdo* do formulário *Artigo: Editar*.

- **Público** Pode ser visualizado por todos - tanto usuários que estão
  logados quanto usuários que não estão logados.
- **Convidado** Este nível de acesso restringe o acesso a usuários que **NÃO**
  estão logados.
- **Registrado** Este nível restringe o acesso a usuários que estão logados.
  Um artigo com o *Acesso* definido como *Registrado* exigirá um login no
  front-end antes que o artigo possa ser visualizado.
- **Especial** Este nível restringe o acesso a usuários que estão logados e
  fazem parte de um grupo de usuários específico, diferente de Registrado.
  Além disso, é possível diferenciar conteúdo que alguns usuários logados
  podem acessar, mas outros não. Tipicamente, isso pode ocorrer em um site
  onde assinaturas são necessárias para acessar conteúdo adicional.
- **Super Usuários** Definir este nível significa que apenas um Super Usuário
  pode acessar o artigo. Isso pode ser usado para artigos sobre gerenciamento
  do site.

Observe que esta lista diz respeito à **Visualização** ou permissão para visualizar
o conteúdo. Você pode criar níveis de Acesso adicionais e Grupos de Usuários para
personalizar quem pode ver o quê.

## Restrição Parcial para Ler Mais

Às vezes, você pode querer restringir o acesso a um artigo, mas permitir acesso irrestrito a uma amostra do artigo. Este é um método comum de disponibilizar conteúdos comerciais pagos. Procedimento:

- Encontre o artigo a ser parcialmente restrito na lista de *Artigos* e abra-o para edição.
- Insira uma *Quebra de Página* após o primeiro parágrafo. A ferramenta de Quebra de Página está próxima ao final da lista de *Conteúdo do CMS* no formulário de edição de artigos do TinyMCE.
- Defina o nível de *Acesso* do artigo como *Registrado*.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.

### Restringindo acesso a Artigos individualmente

Abra o item de menu *Blog da Categoria* ou *Artigos em Destaque* onde o artigo aparecerá.

- Na aba **Opções**, defina **Links Não Autorizados** como **Sim**. Está no final da lista de Opções.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.

### Restringindo acesso a Artigos Globalmente

* Defina as Categorias relevantes para o nível de visualização *Público*, caso contrário, os itens de menu não estarão visíveis para usuários não logados.
* Defina os artigos nas Categorias relevantes para o nível de visualização Registrado. Isso pode ser feito selecionando os artigos e usando o botão *Lote*.
* Vá para **Conteúdo → Artigos → Opções**
* Defina **Links Não Autorizados** como **Sim** na aba Artigos. Se definido como Sim, links para conteúdos registrados serão mostrados, mesmo que você não esteja logado. Você precisará fazer login para acessar o item completo.

**Nota:** Texto em um Artigo sem uma quebra de *Ler Mais* é tratado como todo o texto de Introdução. Se você tiver um Artigo que deve ser restrito apenas para usuários Registrados, mas não tiver uma quebra de Ler Mais, então o artigo inteiro estará visível para todos os usuários. Portanto, adicione um Ler Mais ao artigo!

*Traduzido por openai.com*

