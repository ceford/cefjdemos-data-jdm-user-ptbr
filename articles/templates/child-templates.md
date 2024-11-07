<!-- Filename: J4.x:Child_Templates / Display title: Templates Filhos -->

## Introdução

Modelos filhos utilizam todos os arquivos de seus modelos pais, exceto por quaisquer arquivos com o mesmo nome que você coloque no modelo filho. Arquivos de modelos filhos não são afetados por atualizações do Joomla. Assim, você pode colocar seu próprio arquivo index.php em um modelo filho e fazer com que ele entregue algo bem diferente do modelo padrão, como posições de módulo extras ou substituições alternativas de extensões.

Um cenário de exemplo: suponha que você queira que algumas de suas páginas apareçam com um tema azul, as cores padrão do Cassiopeia, e outras páginas apareçam com um tema verde. Uma maneira fácil de fazer isso é com um modelo filho que utiliza sua própria folha de estilo user.css,

## Exemplo Trabalhado

Começando a partir de **Sistema → Painel de Modelos → Modelos do Site**

- Selecione *Detalhes e Arquivos do Cassiopeia*.
- Selecione o botão *Criar Modelo Filho*.
- Preencha o diálogo pop-up do Modelo Filho e selecione o botão Criar
  Modelo Filho:

![formulário de criação de modelo filho modal](../../../en/images/templates/child-templates-create-green.png)

A seleção de Cassiopeia - Padrão no campo Estilos de Modelos Adicionais
parece desnecessária (isso é um bug?).

- Selecione *Fechar* na Barra de Ferramentas para fechar o formulário do modelo pai.
- Selecione o novo modelo, *Detalhes e Arquivos Cassiopeia_green*, da lista de Modelos.

Nesta fase, há uma estrutura de pastas, mas apenas um arquivo:
templateDetails.xml. Esse arquivo pode ser alterado se você quiser modificar
aspectos da configuração do modelo, por exemplo, posições de modelo a serem
adicionadas ou removidas.

### Criar um arquivo user.css

- Selecione o botão *Novo Arquivo* na Barra de Ferramentas.
- No formulário *Criar ou Enviar um novo arquivo*, certifique-se de selecionar a
  pasta `css`.
- Preencha o nome do arquivo com `user`. NÃO adicione um sufixo!
- Selecione o Tipo de Arquivo `.css`.
- Selecione o botão *Criar*.

![formulário de criação de css do usuário do modelo filho](../../../en/images/templates/child-templates-create-green-user-css.png)

O arquivo user.css está vazio, pronto para que você insira alguns estilos personalizados.
Insira o seguinte para começar o tema verde:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
    a, a:hover, a:focus {
      color: darkgreen;
    }
    .btn-info {
        background-color: darkgreen;
        border-color: #30638d;
        color: #fff;
    }
    .btn-primary, .btn-primary:focus, .btn-primary:hover {
        background-color: darkgreen;
        border-color: var(--cassiopeia-color-hover);
    }

    .btn-check:focus + .btn-info, .btn-info:focus, .btn-info:hover {
        background-color: darkgreen;
        border-color: #264f71;
        color: #fff;
    }
```
Pode ser necessário voltar a este arquivo user.css para adicionar mais estilos
posteriormente.

- Selecione *Salvar & Fechar* ou, separadamente, *Salvar* e depois *Fechar Arquivo*.
- Selecione *Fechar* para fechar o formulário de Personalização.

### Item de Menu

Nesta fase, é necessário um item de menu para utilizar o modelo filho. Uma
nova instalação do Joomla 4 possui o Menu Principal na posição da barra lateral
direita com um item. Esse parece ser um bom lugar para um novo item de menu.

- Selecione **Menus → Menu Principal** no menu do Administrador.
- Selecione o botão *Novo* na Barra de Ferramentas.
- Insira um título apropriado, *Artigos Destacados Verdes* parece
  apropriado neste caso.
- Selecione o botão **Tipo de Item de Menu → Selecionar**.
- Selecione um tipo de item de menu do diálogo pop-up de Tipo de Item de Menu -
  Artigos Destacados neste exemplo.
- Selecione *cassiopeia_manual - Padrão* no campo de formulário *Estilo de Modelo*.

![formulário de edição do item de menu do modelo filho](../../../en/images/templates/child-templates-create-green-menu-item.png)

- Para os propósitos da captura de tela seguinte, o Layout de Blog foi
  configurado para Artigos de Destaque: 0, Artigos de Introdução: 3 e
  Direção de Coluna Múltipla: Cruzada.

### Visualização do Site

- Na página inicial do seu site, selecione o item de menu recém-criado.

![site mostrando o modelo de tema verde personalizado](../../../en/images/templates/child-templates-green-site-result.png)

### Editar o Estilo

- Selecione **Sistema → Painel de Modelos → Estilos de Modelos do Site**
  no menu do Administrador.
- Selecione *Cassiopeia_green - Padrão* na lista de Estilos.
- Altere o Nome do Estilo para *Cassiopeia Verde*. Isso apenas organiza o
  nome conforme aparece nas listas.
- Selecione *Salvar e Fechar*.

*Traduzido por openai.com*

