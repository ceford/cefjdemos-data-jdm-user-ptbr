<!-- Filename: J4.x:Site_Offline / Display title: Site Fora do Ar -->

## Apenas Usuários do Site

Pode haver ocasiões em que você precise tornar seu site Joomla! indisponível para visitantes por um curto período. Para isso, há um simples interruptor de configuração **Site Offline** que pode ser mudado de **Não** para **Sim**, conforme necessário. Quando configurado para *Sim*, todos os visitantes do site verão uma página de mensagem offline com um formulário de login. O formulário padrão offline pode ser personalizado com uma imagem:

![Tela do site offline](../../../en/images/configuration/site-offline.png)

O interruptor Site Offline não se aplica à interface do administrador, e usuários que podem fazer login no backend podem continuar a acessar o frontend. O login no frontend é negado apenas aos usuários nos grupos de usuários Registrado, Autor, Editor e Publicador.

## Para Alternar Offline

- Selecione **Painel Principal → Configuração Global** no menu do Administrador.
- Na aba **Site**, ajuste o botão **Site Offline** para **Sim**.
- Você pode então escolher usar:
  - **Usar Mensagem Personalizada**, que é o texto na caixa de Mensagem Personalizada. Ou...
  - **A Mensagem Padrão do Idioma do Site**, que é **Este site está fora do ar 
    para manutenção. Por favor, volte novamente em breve.** em inglês ou o equivalente 
    no idioma selecionado do Site. Isso também permite a seleção de uma imagem. Ou...
  - **Ocultar** para não mostrar nenhuma mensagem.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.
- Realize a manutenção necessária.
- Retorne ao formulário de Configuração Global.
- Ajuste o botão de Site Offline para **Não**.
- Selecione **Salvar & Fechar** na Barra de Ferramentas.

## Todos os Usuários

Você pode limitar o acesso ao seu site protegendo com senha o diretório do Joomla. Apenas usuários que conhecem o nome de usuário e a senha de acesso ao diretório poderão acessar o site. Você pode configurar mais de um usuário assim. Com o Painel de Controle de Hospedagem cPanel:

- Faça login na sua conta cPanel.
- Na seção Arquivos, selecione **Privacidade de Diretório**.
- Se a raiz do seu site estiver em um subdiretório do public_html
  - Selecione o diretório public_html.
- Selecione o botão Editar para o diretório que contém seu site (public_html se seu site estiver na raiz da web).
- Marque a caixa de seleção **Proteger este diretório com senha.**
- Insira um nome para o diretório protegido: o padrão pode ser suficiente.
- Selecione o botão **Salvar**.
- Aparecerá uma página de mensagem de Sucesso com um link Voltar, selecione-o.
- Crie um usuário para acesso ao diretório protegido.
- Insira um nome de usuário.
- Insira uma senha e repita (lembre-se dela ou anote-a).
- Selecione **Salvar**.

Agora, verifique se o diretório exige uma senha para acesso via web. Quando você visitar seu site, será solicitado o nome de usuário e a senha de acesso ao diretório. Eles podem ser completamente diferentes do seu nome de usuário e senha do Joomla.

Para remover a proteção por senha do diretório:

- Faça login na sua conta cPanel.
- Na seção Arquivos, selecione **Privacidade de Diretório**.
- Se a raiz do seu site estiver em um subdiretório do public_html
  - Selecione o diretório public_html.
- Selecione o botão **Editar** para o diretório que contém seu site (public_html se seu site estiver na raiz da web). Agora mostrará um símbolo de cadeado e Sim sob o título Privado.
- **Desmarque** a caixa de seleção **Proteger este diretório com senha.**
- Selecione o botão **Salvar**.

Para verificar se a proteção por senha foi removida, use um navegador diferente para acessar seu site ou feche e reabra seu navegador existente e acesse seu site novamente.

*Traduzido por openai.com*

