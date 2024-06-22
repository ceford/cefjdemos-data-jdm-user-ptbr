<!-- Filename: J3.x:Updating_Joomla_(Update_Method) / Display title: Atualizando o Joomla (Método de Atualização) -->

Este é o método recomendado de atualização para sites no CMS Joomla.

Não apenas este é o método recomendado, como também é o método mais
fácil de atualizar o CMS Joomla. Ele também é chamado de ***Atualização
com um clique***. Se você não conseguir utilizá-lo devido a questões
específicas de uso (distribuições, linguagens, velocidade de servidor),
você pode atualizar o CMS Joomla usando o ** método de
instalação**.

Este método é adequado para

- Todas as versões do CMS Joomla **3.x.x** para **3.x.x** - atualizações
  (atualização de manutenção)

Este método não é adequado para

- CMS Joomla **3.1.2** para **≥ 3.1.3** - veja [Instruções Especiais
  para Atualização da Versão
  3.1.2](https://docs.joomla.org/J3.x:Detailed_instructions_for_updating_from_3.1.2_to_3.1.4 "Special:MyLanguage/J3.x:Detailed instructions for updating from 3.1.2 to 3.1.4")

## Como atualizar

Você precisa atualizar a sua instalação Joomla? Se uma atualização
estiver disponível, haverá uma mensagem indicando a atualização e um
botão para clicar.

<img
src="https://docs.joomla.org/images/thumb/3/35/J3-update-control-panel-notify-en.PNG/450px-J3-update-control-panel-notify-en.PNG"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/3/35/J3-update-control-panel-notify-en.PNG 1.5x"
data-file-width="571" data-file-height="331" width="450" height="261"
alt="J3-update-control-panel-notify-en.PNG" />

Você também verá um aviso na parte inferior da 'barra lateral esquerda'.

<img
src="https://docs.joomla.org/images/a/a2/J3-update-control-panel-notify-alternative-en.PNG"
class="thumbborder" decoding="async" data-file-width="229"
data-file-height="209" width="229" height="209"
alt="J3-update-control-panel-notify-alternative-en.PNG" />

O Joomla irá notificá-lo em sua página Administrator (Painel de
Controle) quando uma atualização estiver disponível. Ele não fará a
atualização para você. É responsabilidade do administrador iniciá-la e
verificar se a atualização foi bem sucedida.

A seguir estão os passos necessários para completar a atualização de sua
instalação do CMS Joomla.

### Passo 1: Backup

Verifique se você tem um **BACKUP ATUAL** do seu site! Em muitos casos,
o seu servidor faz backups periódicos do site. **NÃO** conte com eles! É
**FORTEMENTE RECOMENDADO** que você faça o seu próprio backup.

### Passo 2: O Componente de Atualização

Você precisará rodar o componente de atualização. Clique no 'botão' de
atualização ou no 'link previamente mostrado na sidebar' ou use o menu
principal, selecione e clique em **Components **→** Joomla! Update**.
Você verá a imagem abaixo.

<img
src="https://docs.joomla.org/images/2/26/J3-joomla-update-component-en.PNG"
class="thumbborder" decoding="async" data-file-width="975"
data-file-height="389" width="975" height="389"
alt="J3-joomla-update-component-en.PNG" />

Selecione 'Gravar arquivos diretamente' (padrão) ou 'Gravar arquivos
utilizando FTP' como o método de upload de novos arquivos do core da sua
instalação. Você fez backup? Consulte o Passo 1 acima.

### Passo 3: Iniciar a atualização

Clique no botão "Instalar a atualização" e a atualização começará.

<img
src="https://docs.joomla.org/images/0/08/J3-updating-your-joomla-files-en.PNG"
class="thumbborder" decoding="async" data-file-width="787"
data-file-height="390" width="787" height="390"
alt="J3-updating-your-joomla-files-en.PNG" />

Quando a atualização for concluída, você verá um aviso de sucesso com a
nova versão.

<img
src="https://docs.joomla.org/images/c/c0/J3-jooml-update-successful-en.PNG"
class="thumbborder" decoding="async" data-file-width="659"
data-file-height="301" width="659" height="301"
alt="J3-jooml-update-successful-en.PNG" />

Quando a atualização for concluída, pode ser necessário limpar o cache
do navegador para ajustar quaisquer alterações de CSS no template.

## Atualizar as configurações do Joomla

Na maioria dos casos, você não terá que alterar essas configurações. As
opções padrão certificam-se de que sua instalação do CMS Joomla será
sempre verificada em relação ao correto servidor de atualização, e a
pessoa apropriada com acesso de administrador pode atualizar a
instalação.

A tela de opções é acessada clicando no botão "Opções" na tela principal
de Atualização Joomla. Uma vez que você clique no botão "Opções", você
verá a seguinte imagem.

<img
src="https://docs.joomla.org/images/1/18/J3-update-component-configure-server-en.PNG"
class="thumbborder" decoding="async" data-file-width="818"
data-file-height="438" width="818" height="438"
alt="J3-update-component-configure-server-en.PNG" />

### Configuração do Servidor de Atualização

O aviso de atualização que você verá no Painel de Controle depende da
configuração do "Servidor de Atualização" e cache.

<img
src="https://docs.joomla.org/images/9/91/J3-update-component-configure-server-options-en.PNG"
class="thumbborder" decoding="async" data-file-width="459"
data-file-height="260" width="459" height="260"
alt="J3-update-component-configure-server-options-en.PNG" />

A primeira opção mostra a atualização mais recente da versão em uso
(padrão). A segunda opção mostra a atualização mais recente da versão
mais atual. O cache pode fazer com que uma atualização disponível não
seja detectada e, por isso, você deve limpá-lo.

### Permissões

<img
src="https://docs.joomla.org/images/f/fe/J3-update-component-configure-server-permissions-en.PNG"
class="thumbborder" decoding="async" data-file-width="846"
data-file-height="494" width="846" height="494"
alt="J3-update-component-configure-server-permissions-en.PNG" />
