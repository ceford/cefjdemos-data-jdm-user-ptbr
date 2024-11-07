<!-- Filename: J4.x:Guest_Access / Display title: Acesso de Convidado  -->

## Níveis de Acesso

Os visitantes do site podem visualizar itens como artigos, módulos e itens de menu, pois esses itens são alocados ao nível de acesso Público por padrão. Este nível de acesso também permite que usuários logados visualizem os mesmos itens de conteúdo. No entanto, há ocasiões em que não é apropriado para um usuário logado visualizar um item de conteúdo. Por exemplo, um item de menu de Login deve ser visto por usuários que não estão logados, mas não por usuários que estão logados. É para isso que serve o nível de acesso Visitante. Usuários logados devem ver um item de menu de Logout em vez disso. Tais itens precisam ser atribuídos ao nível de acesso Registrado.

Em alguns casos, também é adequado restringir o acesso a um artigo ou módulo para usuários que não estão logados ou para usuários que estão logados.

## Acesso de Convidado

O uso do nível de acesso de Convidado pode ser ilustrado com um item de menu de Login:

- Selecione **Menus → Menu Principal → +** no menu do Administrador. Use o menu que preferir para os novos itens.
- No formulário **Menus: Novo Item**, insira um título adequado no campo **Título**, por exemplo, **Login**.
- No campo **Tipo de Item de Menu**, use o botão **Selecionar** para abrir o diálogo pop-up do Tipo de Item de Menu.
- Na lista **Tipo de Item de Menu**, selecione a seção Usuários e escolha o item **Formulário de Login**.
- De volta ao formulário **Menus: Novo Item**, defina o campo **Acesso** para **Convidado**.
- Salvar
- Opcionalmente, selecione a lista de Ordenação e escolha o item **após** o qual você gostaria que o item de Login aparecesse.

![formulário de menu de login restrito ao acesso de convidado](../../../en/images/users/guest-access-menu-login.png)

- Salvar e Fechar.
- Visualize o site. Verifique se o item de menu de Login funciona. Verifique se ele desaparece após o login.

## Acesso Registrado

O uso do nível de acesso Registrado pode ser ilustrado com um item de menu de Logout:

- Selecione **Menus → Menu Principal → +** no menu do Administrador. Use o menu que preferir para os novos itens.
- No formulário **Menus: Novo Item**, insira um título adequado no campo **Título**, por exemplo, **Logout**.
- No campo **Tipo de Item de Menu**, use o botão **Selecionar** para abrir o diálogo pop-up de Tipo de Item de Menu.
- Na lista **Tipo de Item de Menu**, selecione a seção Usuários e selecione o item **Logout**.
- De volta ao formulário **Menus: Novo Item**, defina o campo **Acesso** para **Registrado**.
- Salve
- Opcionalmente, selecione a lista suspensa de Ordenação e escolha o item **após** o qual você gostaria que o item de Login aparecesse.

![formulário de menu de logout restrito ao acesso registrado](../../../en/images/users/guest-access-menu-logout.png)

- Salve e Feche.
- Visualize o site. Verifique se o item de menu Logout funciona. Verifique se ele desaparece após o logout.

*Traduzido por openai.com*

