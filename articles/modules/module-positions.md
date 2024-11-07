<!-- Filename: J4.x:Module_Positions / Display title: Posições do Módulo  -->

## Introdução

As posições dos módulos do template são definidas em um arquivo templateDetails.xml e usadas em um arquivo index.php do template. Vários módulos podem ser atribuídos a uma única posição, por isso raramente há necessidade de criar mais posições. Se você quiser mais posições, precisará criar seu próprio template, o que não está abordado aqui.  

## Visualizar Posições dos Módulos

Há uma opção no template que permite ver as localizações dos módulos nos templates do Site e do Administrador, incluindo posições que não têm módulos atribuídos. Para habilitar este recurso:

- Selecione **Sistema** → **Templates do Site** no menu do Administrador.
- Selecione o botão `Opções` na Barra de Ferramentas.
- No formulário de Opções do Template, defina **Visualizar Posições dos Módulos** como **Habilitado**.
- Salve e Feche.

Para visualizar as posições dos módulos, você precisa adicionar ?tp=1 ou &tp=1 ao URL.

- Se o URL não contiver um ponto de interrogação, adicione ?tp=1.
- Se o URL já contiver um ponto de interrogação, adicione &tp=1.

### Posições do Template do Administrador Atum

![posições de template atum](../../../en/images/modules/template-positions-templates-page.png)

### Posições do Template do Site Cassiopeia

![posições de template cassiopeia](../../../en/images/modules/template-positions-site-page.png)

Você também pode achar este diagrama das posições do módulo útil:

![diagrama de posições do template cassiopeia](../../../en/images/modules/cassiopeia-template-positions.png)

## Locais de Produção

Lembre-se de alterar as **Posições do Módulo de Visualização** para **Desativado** em sites de produção.

*Traduzido por openai.com*

