<!-- Filename: Joomla_3.x_to_4.x_Step_by_Step_Migration / Display title: Joomla 3 para 4 Passo a Passo -->

## Introdução

**Aviso:** Este guia assume que você está começando no Joomla 3.10.x. Se você está em uma versão anterior, certifique-se de atualizar para o Joomla 3.10 primeiro antes de passar para o Joomla 4. Não há pressa. Certifique-se de que todas as suas extensões estão prontas para o Joomla 4.x. O Joomla 3.10.x é suportado até 16 de agosto de 2023.

A seguir estão as instruções passo a passo para migrar um site 3.10.x para o Joomla! 4.x. Embora existam centenas de cenários diferentes, estas instruções darão a você o procedimento básico a ser seguido. Migrações muito complexas provavelmente serão resultado de extensões de terceiros instaladas. É recomendável entrar em contato com os desenvolvedores das extensões de terceiros instaladas no seu site Joomla para obter suas sugestões de como migrar suas extensões.

## Passo a Passo

### Configuração de um Local de Desenvolvimento

1. Certifique-se de que você está executando a versão mais recente do Joomla 3.10.x antes de prosseguir.
2. Faça um backup do seu site ao vivo 3.10.x. Você pode usar uma ferramenta sugerida (veja as *Ferramentas Sugeridas* no final da página) ou pode fazer isso manualmente.
   - [Noções Básicas de Backup para um Site Joomla!](https://docs.joomla.org/Special:MyLanguage/Backup_Basics_for_a_Joomla!_Web_Site)
   - [Quais são as melhores práticas para backups de site?](https://docs.joomla.org/Special:MyLanguage/What_are_the_best_practices_for_site_backups%3F)
3. Certifique-se de que seu ambiente atenda aos [requisitos técnicos para o Joomla 4](https://downloads.joomla.org/technical-requirements) antes de prosseguir.
4. Crie um novo banco de dados e novo usuário para restaurar seu site 3.10.x.
5. Crie um site de testes ou área de construção para trabalhar e restaure a cópia de backup do seu site 3.10.x em um dos seguintes locais:
   - Um subdomínio.
   - Um subdiretório.
   - Um dispositivo local. O Joomla tem um tutorial detalhado sobre a instalação do XAMPP. No entanto, [WAMP](https://www.wampserver.com/en/), [MAMP](https://www.mamp.info/en/windows/) e [LAMP](https://sourceforge.net/projects/lampas/) são alternativas adequadas.
   - Uma nova conta de hospedagem em um domínio temporário na raiz. (Se você gostaria de mudar de hospedagem durante o processo de migração.)
     - Restaurando um site em um dispositivo local.
       Veja [Instalando Joomla localmente](https://docs.joomla.org/Special:MyLanguage/Installing_Joomla_locally) e [Configurando sua estação de trabalho para desenvolvimento Joomla](https://docs.joomla.org/Special:MyLanguage/Setting_up_your_workstation_for_Joomla_development).
     - Restaurando um site com uma ferramenta listada no final da página. (Leia a documentação do desenvolvedor.)
6. No seu local de teste, atualize sua instância Joomla! 3.10.x para a versão de manutenção mais recente.
7. Certifique-se de que você tem o esquema de banco de dados mais recente atualizado para a versão mais recente 3.10.x, indo na aba **Gerenciador de Extensões → Banco de Dados**. Se seu esquema não estiver atualizado, como na imagem a seguir, clique no botão **Corrigir**:<br> ![joomla 3 extensões banco de dados](../../../en/images/migration/admin-extension-database-fix.png)
8. Esvazie a lixeira: você tem algum artigo na lixeira? Se sim, exclua-os (e qualquer mídia aplicável que possa estar associada a eles, se não estiver em uso em outro lugar no site). Artigos (categorias e itens de menu também) deixados na lixeira podem causar problemas na conclusão de uma migração sem erros.
9. Teste.
10. Faça backup novamente.

### Avaliar Cada Extensão

No seu planejamento, você determinou quais extensões de terceiros iriam ficar ou sair e como elas serão migradas. Para esta parte do passo a passo, você usará extensivamente duas seções diferentes do site: o *Verificador Pré-Atualização* em **Componentes → Atualização do Joomla** e **Extensões → Gerenciar → Gerenciar**. Você vai analisar cada extensão instalada no seu site. Você determinará se elas precisam ser atualizadas para a versão mais recente ou desinstaladas. Mais detalhes em [Verificador Pré-Atualização](https://docs.joomla.org/Special:MyLanguage/:Pre-Update_Check).

1. Usando o **Verificador Pré-Atualização**, você precisará configurar o componente de Atualização do Joomla para Joomla 4. Para fazer isso, siga:
2. Vá para **Componentes → Atualização do Joomla**. Deve dizer que nenhuma atualização foi encontrada. Se não disser, atualize o Joomla para a versão mais recente (deve ser 3.10.x) e teste. Em seguida, faça outro backup. Clique no botão Opções no canto superior direito.
3. Selecione *Joomla Próxima* na lista suspensa para Canal de Atualização.<br> ![opções de atualização seleção de canal](../../../en/images/migration/update-options-channel.png)
4. Clique em **Salvar & Fechar**.
5. Você verá então sua versão do Joomla instalada, a versão mais recente do Joomla e a URL para o pacote de atualização. O Joomla irá mostrar novamente os requisitos para o Joomla 4. Se sinalizar que você tem um sistema incompatível ou extensões, ele te informará aqui. Dedique um momento para revisar esta página. <br> ![atualizar para 4 pré-verificação de atualização](../../../en/images/migration/update-to-4-pre-update-check.png)
   <div class="alert alert-warning"><strong>Aviso:</strong> Não atualize para o Joomla! 4 agora. Isto é apenas para preparar suas extensões de terceiros e deixar o site compatível com o Joomla! 4.</div>
6. Veja o Verificador Pré-Atualização e o Verificador Pré-Atualização de Extensão na aba Verificador Pré-Atualização do componente de Atualização do Joomla. Se qualquer extensão que não está no seu planejamento for listada aqui, adicione-a à sua lista de extensões a serem investigadas.
7. Se você migrou do Joomla! 2.5 para 3.x no passado, pode haver algumas extensões remanescentes que precisam ser limpas. As seguintes são extensões mais antigas do 2.5 ou 3.x que precisam ser desinstaladas antes de atualizar para o Joomla 4:
   - plg_content_geshi
   - Template de Administrador Bluestork
   - Beez_20
   - Beez5
   - Atomic
   1. Quando se trata de templates, desinstale todos os templates frontend ou backend principais, exceto Protostar e Beez3 (templates frontend) e Isis ou Hathor (templates de administrador). **NOTA: Protostar NÃO é compatível com o Joomla 4**. Após a migração, ele desaparecerá. Você precisará ter um template selecionado como *padrão* e pode usar Protostar ou Beez3. Protostar desaparecerá após a migração para o Joomla 4.x.
   2. Se você encontrar outros arquivos que precisam ser desinstalados, adicione-os a esta página. Esta é uma wiki, então qualquer um pode adicionar à página. Agradecemos antecipadamente pelo seu serviço.
8. Você notará as tags que indicam se uma extensão é compatível ou não. Essas tags geralmente dão uma indicação verdadeira se elas dizem Não ou Sim. Se disserem *Tag de Compatibilidade Faltando*, significa que o desenvolvedor da extensão não usou uma tag na extensão, então não sabemos se ela é ou não compatível com o Joomla 4. Fale com o desenvolvedor para verificar.
9. **Atualizar Extensões:** atualize qualquer extensão que você vai manter em seu site. No Joomla! 3.10.x, você pode ir para **Gerenciador de Extensões → Aba de Atualização** e clicar em **Procurar Atualizações**, o que adicionará uma dica de ferramenta na coluna Versão, sob a aba Gerenciar, fornecendo algumas informações de compatibilidade do backend. Esta funcionalidade só suporta extensões que atualizam via aba de Atualização do Gerenciador de Extensões. Se você tiver extensões instaladas que não usam a atualização de extensões do Joomla, elas precisam ser avaliadas manualmente conforme detalhado abaixo. O mesmo vale para aquelas extensões que têm uma dica de ferramenta. Você ainda precisará verificar o tipo de pacote e caminho de migração com o desenvolvedor da extensão para verificar como atualizar/migrar.
10. Investigue e Desinstale Extensões: vá para **Gerenciador de Extensões → Gerenciar**
11. Clique no Botão *Ferramentas de Pesquisa* para mostrar as opções de filtro.
12. Selecione Pacote na lista suspensa *Selecionar Tipo*.<br> ![página de gerenciar extensões](../../../en/images/migration/extensions-manage.png)
    <div class="alert alert-info">Selecionar Pacote primeiro é recomendado porque, se houver algo que você precise desinstalar em um pacote, ele desinstalará automaticamente os Módulos, Plugins ou qualquer outra coisa associada no pacote de uma só vez.</div>
13. Desinstale qualquer Pacote que não seja mais necessário ou que não será migrado para o Joomla 4.
14. Repita este processo de passar pela aba Gerenciar para todos os Tipos na lista suspensa: Componente, Arquivo, Idioma, Biblioteca, Módulo, Plugin e Template. Se o Autor mencionar Projeto Joomla!, então deixe essas extensões quietas. Para todos os outros, certifique-se de que você desinstale aqueles que não estão em uso ou não são compatíveis com o Joomla! 4.x.
    <div class="alert alert-danger"><strong>NOTA!</strong> Você não poderá desinstalar qualquer template que esteja definido como padrão. Você precisará selecionar um template Suportado pelo Core como Beez3 ou Protostar e então desinstalar o template se precisar fazer isso. <em>Outro lembrete:</em> <strong>Protostar não é compatível com o Joomla 4</strong>. Após a migração, ele desaparecerá. Selecionar como padrão apenas leva você ao Joomla 4.x.</div>
15. Faça uma nota de qualquer versão dos Pacotes e Componentes atualmente em execução que você manterá em seu site. Você pode copiá-los/colá-los em um documento para referência.
16. Para qualquer extensão que você esteja mantendo, mas que não usa o Gerenciador de Extensões para atualizar com um clique (**Extensões → Gerenciar → Atualizar**), atualize todas as extensões para as versões mais recentes.
17. Antes e enquanto você atualiza, verifique se as extensões têm versões 3.10.x & 4.x no mesmo pacote. Se sim, elas estarão bem para *atualizar com um clique*. Se não, e 3.10 e 4.x têm pacotes diferentes, você precisará analisá-las caso a caso. Elas normalmente se enquadram em um dos seguintes cenários:
    - A extensão tem pacotes separados, mas ao atualizar para 4.x, detectam isso automaticamente e ainda funcionam. Certifique-se de que o desenvolvedor confirme isso.
    - A extensão tem pacotes separados que precisam ser desinstalados em 3.10.x e depois instalados com a versão do Joomla 4.x uma vez que o site é migrado. Um exemplo disso pode ser um plugin de conteúdo. É muito simples desinstalá-lo em 3.10.x e, em seguida, instalá-lo novamente em 4.x.
    - Veja [Considerações sobre Templates](https://docs.joomla.org/Special:MyLanguage/Template_Considerations_During_Migration) para obter mais informações específicas sobre templates e [Convertendo um template de versão anterior do Joomla](https://docs.joomla.org/J3.x:Converting_A_Previous_Joomla!_Version_Template).

#### Notas sobre a Pesquisa (com_search)

A Pesquisa (com_search) será desacoplada no Joomla 4.x. A Pesquisa (com_search) migrará para o Joomla 4. Após a migração, você precisará atualizá-la para a versão Joomla 4.x via com_installer. Ela continuará a ser mantida, mas mais como uma extensão de terceiros, recebendo atualizações via com_installer. É recomendado usar a Pesquisa Inteligente (com_finder) daqui em diante. A Pesquisa ainda está disponível no [Diretório de Extensões Joomla](https://extensions.joomla.org/category/official-extensions/).

#### Notas sobre Weblinks

Weblinks foi desacoplado no Joomla 3.4. Se estava em uso em um site 2.5, o processo de migração notaria isso e migraria o componente Weblinks e os dados. Para a migração do 3.10.x para 4.x, será o mesmo. Ele ainda está disponível e mantido na JED em [Extensões Oficiais](https://extensions.joomla.org/category/official-extensions).

#### Notas sobre Roteamento Legado

O roteamento legado não estará disponível no Joomla 4.x. Apenas o Moderno estará disponível. Quando você fizer a migração, se estiver usando roteamento legado, o sistema automaticamente mudará para o roteamento Moderno. Você vai querer rodar um verificador de links quebrados no seu site após migrar para o Joomla 4.x e *antes de ir ao ar*.

### Migração para o Joomla! 4.x

Uma vez que você tenha atualizado ou desinstalado suas extensões de terceiros de forma que apenas aquelas compatíveis com o Joomla! 4 permaneçam em sua instalação, continue com os seguintes passos:

1. Vá para **Sistema → Configuração Global → Aba Servidor** e altere a Relatório de Erros de Padrão do Sistema para Máximo. Certifique-se de Salvar & Fechar. <br> ![configuração global do sistema aba servidor](../../../en/images/migration/system-global-configuration-server-tab.png)
2. Faça outro backup.
3. Vá para **Componentes → Atualização do Joomla**. (Deve dizer que nenhuma atualização foi encontrada. Se não disser, atualize o Joomla para a versão mais recente e teste. Depois faça outro backup.) Clique no botão Opções no canto superior direito.
4. Selecione *Joomla Próxima* na lista suspensa para Canal de Atualização.<br> ![componente atualização do joomla selecionar canal de atualização](../../../en/images/migration/update-select-channel.png)
5. Clique em **Salvar & Fechar**.
6. Você verá então sua versão do Joomla instalada, a versão mais recente do Joomla! e a URL para o pacote de atualização. O Joomla mostrará novamente os requisitos para o Joomla 4. Se sinalizar que você tem um sistema ou extensões incompatíveis, ele te informará aqui. Dedique um momento para revisar esta página.<br> ![verificação de atualização para joomla 4](../../../en/images/migration/update-check.png)
7. Se a atualização não estiver aparecendo, vá para **Gerenciador de Extensões → Atualizar** e pressione Purge Cache na barra de ferramentas. Agora a atualização para o Joomla! 4 deve aparecer.
8. Cruze os dedos e certifique-se de que você tem esse backup disponível em caso de necessidade.
9. Clique no botão Instalar a Atualização.
10. Faça chá enquanto a barra de status carrega até ficar completamente verde. O tempo que isso leva depende do seu site, conexão de Internet e velocidade do servidor. O processo leva cerca de dois minutos. Quando a atualização estiver concluída, você provavelmente será desconectado do Administrador. Faça o login novamente. Duas vezes.
11. Se tudo correr bem, você verá uma aparência totalmente nova no painel do administrador do backend.<br> ![joomla 4 ou 5 painel inicial](../../../en/images/migration/j4-home-dashboard.png)
12. Vá para **Sistema → Manutenção → Banco de Dados** e clique em *Corrigir* se aparecerem erros.
13. Em **Sistema → Instalar → Descobrir** veja se há alguma extensão para instalar. (Não deve haver nenhuma!)
14. Vá para o frontend do seu site e veja se ele aparece, mesmo que não seja o template correto. Se sim, continue. Se não, veja os erros comuns durante a migração.
15. Faça um backup.
16. Instale seu novo template ou outras extensões se os tiver para instalar. Faça backups frequentemente.
17. Configure-os. Faça backups frequentemente.
18. Execute um verificador de links quebrados e corrija qualquer link quebrado.
19. Teste tudo. Faça backups frequentemente.
20. Se tudo funcionar como esperado, mude Relatório de Erros de volta para Padrão do Sistema (**Sistema → Configuração Global → Aba Servidor**). Certifique-se de **Salvar & Fechar**.

### Indo ao Ar com seu Site Joomla! 4.x

1. Quando estiver pronto para ir ao ar, faça backup do seu site 3.10 pela última vez. Restaure em um subdiretório ou subdomínio se desejar.
2. Faça backup do seu site Joomla! 4.x e mova ou restaure seu site Joomla! 4.x para a raiz (ou altere os servidores de nomes se você estava construindo em um domínio temporário em uma nova raiz de conta de hospedagem).
3. Teste novamente.
4. SE você fez alterações de segurança no arquivo .htaccess no passado, pode ser necessário alterar uma linha (ou linhas) nele para atualizar para a próxima versão do Joomla 4. Por favor, vá para [Mudanças no Htaccess após o Joomla 4](https://docs.joomla.org/Htaccess_changes_after_joomla4.0.4) para determinar se você precisa alterar seu arquivo ou não.
5. Remova o site Joomla! 3.10 do servidor dentro de alguns dias, a menos que você tenha editado seu arquivo *robots.txt* para bloquear os motores de busca.
6. Remova todos os sites de desenvolvimento com os quais você esteve trabalhando ou mantenha-os atualizados se estiverem executando uma versão atual para evitar tentativas de hacking no seu servidor.

Se você teve alterações de dados no site 3.10 enquanto estava migrando para 4.x, você vai querer mover esses dados para o site 4.x antes de ir ao ar. Você pode fazer isso manualmente (certifique-se de manter os mesmos IDs de usuário - siga a ordem) ou usando uma [extensão de terceiros](https://extensions.joomla.org/category/migration-a-conversion/data-import-a-export%20transfer%20tool/third-party%20extension/).

## Ferramentas Sugeridas

- [Akeeba Backup](http://extensions.joomla.org/extensions/access-a-security/site-security/backup/1606)
  é muito popular para backup e restauração.
- Mais [ferramentas de backup](https://extensions.joomla.org/tags/backup/).

*Traduzido por openai.com*

