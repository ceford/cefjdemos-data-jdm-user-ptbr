<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Joomla 5 para 6 passo a passo",
    "description": " ",
    "author": ""
}
-->

<div class="alert alert-warning">
<p class="h3">Aviso</p>

Este guia pressupõe que você está começando com o Joomla 5.4.x. Se estiver em uma versão anterior, certifique-se de migrar ou atualizar para o Joomla 5.4.x antes de atualizar para o Joomla 6.x.
</div>

## Introdução

Boas notícias para quem está passando do Joomla 5.4.x para o 6.x: é uma atualização, não uma migração. Por quê? Por dois motivos principais:

- As extensões do Joomla 5 (J5) que removeram todas as partes de código obsoletas, usam código atualizado do Joomla e não exigem que o plugin Comportamento - Compatibilidade retroativa esteja ativado funcionarão no Joomla 6 (J6)
- A maioria das outras funcionará com o novo plugin Comportamento - Compatibilidade retroativa 6 ativado

Esta documentação reflete o processo mais simples, combinando o planejamento e o passo a passo em um único documento. Ainda assim, você precisará de alguns conhecimentos. Consulte a [[Migration Step by Step Self Assessment|Autoavaliação]] para determinar se você deve ou não realizar a atualização por conta própria.

<div class="alert alert-info">
<p class="h3">Documentação para desenvolvedores de extensões de terceiros sobre o Joomla 5.4 para 6.0.</p>

- [Removido e incompatibilidade retroativa](https://manual.joomla.org/60/removed-backward-incompatibility)
- [Novas obsolescências](https://manual.joomla.org/60/new-deprecations)
- [Sobre a documentação de migrações](https://manual.joomla.org/migrations)
- [Novos recursos](https://manual.joomla.org/60/new-features/)
</div>

## Planejamento do 5.4.x para o 6.x

### Especificações de hospedagem/técnicas

1. Determine se o seu ambiente de hospedagem atende aos requisitos. Você não poderá atualizar para o Joomla 6 se o ambiente do seu servidor não atender aos [requisitos técnicos](https://manual.joomla.org/docs/get-started/technical-requirements/) mínimos. A opção de atualização não aparecerá no componente Atualização do Joomla.
    - PHP 8.3
    - MySQL 8.0.13
    - MariaDB 10.6.x
    - PostgreSQL 14.0

Você pode verificar as informações do sistema no site Joomla 5 clicando em Sistema -> Informações do sistema. Entre em contato com o seu provedor de hospedagem se o seu servidor não atender aos requisitos.

![Painel do sistema com o link Informações do sistema destacado](../../../en/images/migration/joomla-5-to-6-steps/01-steps-5-to-6-system-dashboard.png)

Veja a seguir um exemplo de ambiente que atende aos requisitos técnicos. Ele mostra MySQL 8.0.43, PHP 8.3, Joomla 5.4.x e o Plugin de compatibilidade retroativa desativado.

![Informações do sistema mostrando a versão do Joomla, a versão do PHP, o tipo de banco de dados, a versão do banco de dados e o Plugin de compatibilidade retroativa desativado](../../../en/images/migration/joomla-5-to-6-steps/02-steps-5-to-6-system-information.png)

2. Verifique se todas as suas extensões são compatíveis com o Joomla 6. Há vários cenários envolvendo extensões de terceiros para esta atualização.

    1. A extensão pode ser compatível com o J5 e o J6 SEM o uso do plugin de compatibilidade retroativa.
    2. A extensão pode ser compatível com o J5 e o J6 COM o uso do plugin de compatibilidade retroativa.
    3. A extensão pode parecer funcionar no J6, mas, quando você tentar usá-la, ela estará com defeito.
    4. A extensão pode danificar todo o site.

Não se preocupe! Não é tão ruim quanto parece! Primeiro, vamos falar sobre os plugins de compatibilidade retroativa.

<div class="alert alert-warning">
<p class="h3">Aviso</p>

Para atualizar do Joomla 5.4.x para o 6.x, o Plugin de compatibilidade retroativa do Joomla 5 DEVE estar DESATIVADO.
</div>

### Os plug-ins de compatibilidade retroativa

O plug-in [Behaviour - Backward Compatibility 6](https://manual.joomla.org/60/compat-plugin/) incluído no Joomla 5.4.x tem como objetivo aprimorar a compatibilidade retroativa entre o Joomla 5 e o Joomla 6. O plug-in ajuda extensões de terceiros a usar classes que não estão mais incluídas no Joomla 6. Ele é implementado como um tipo de plug-in "Behaviour" para garantir que seja carregado antes de qualquer outro plug-in.

![Página de plug-ins mostrando os plug-ins de compatibilidade retroativa](../../../en/images/migration/joomla-5-to-6-steps/03-steps-5-to-6-bc-plugins.png)

A imagem acima mostra dois plug-ins de compatibilidade retroativa:

1. Behaviour - Backward Compatibility e
2. Behaviour - Backward Compatibility 6

O plug-in Behaviour - Backward Compatibility (sem um número no nome do plug-in) é fornecido com o Joomla 4.4.x para criar uma camada de compatibilidade retroativa para extensões do Joomla 5. **Esse plug-in deve ser desativado antes da atualização para o J6**.

O plug-in Behaviour - Backward Compatibility 6 é fornecido com o Joomla 5.4.x para criar uma camada de compatibilidade retroativa para extensões do Joomla 6.

Eles não podem estar ambos ativados durante a atualização para o J6.

Antes de atualizar do Joomla 5 para o Joomla 6, o plug-in Behaviour - Backward Compatibility (sem um número no nome do plug-in) deve ser desativado. Você precisa garantir que todas as extensões de terceiros possam ser executadas no seu site sem que o plug-in Behaviour - Backward Compatibility esteja ativado antes de poder atualizar para o J6.

Depois de determinar que todas as extensões de terceiros são compatíveis e totalmente funcionais no J5 sem que o plug-in Behaviour - Backward Compatibility esteja ativado, você poderá desativá-lo. Dito isso, recomendamos cautela. Antes de desativar o plug-in de compatibilidade retroativa, sugerimos fazer uma das duas coisas a seguir:

1. Faça isso em um site de desenvolvimento/teste. Dessa forma, se você acidentalmente deixar passar alguma extensão que torne o backend inacessível, isso não fará com que seu site de produção fique indisponível.
2. Certifique-se de ter acesso ao banco de dados. Dessa forma, você poderá ativar novamente o plug-in rapidamente por meio do banco de dados, se necessário. Mais informações abaixo.

Ao realizar uma atualização para o J5.4.x, o plug-in Behaviour - Backward Compatibility 6 será ativado automaticamente. Em novas instalações do J6, o plug-in de compatibilidade retroativa será desativado por padrão.

O plug-in Behaviour - Backward Compatibility 6, que oferece suporte a extensões que funcionam no J5, permanecerá disponível durante todo o J6. No J7, as extensões do J5 não terão compatibilidade retroativa por meio do plug-in. Isso dá aos desenvolvedores de extensões mais dois anos para tornar suas extensões compatíveis com o J6 sem o plug-in de compatibilidade retroativa. A intenção é que, a cada lançamento de ciclo de vida, um plug-in de compatibilidade retroativa ofereça suporte ao ciclo de vida anterior até o ciclo de vida seguinte.

É possível desativar o plug-in Behaviour - Backward Compatibility 6 no J6? Excelente pergunta. Depois de determinar que todas as suas extensões de terceiros são compatíveis e totalmente funcionais sem que o plug-in de compatibilidade retroativa esteja ativado, você poderá desativar o plug-in Behaviour - Backward Compatibility 6. Dito isso, recomendamos cautela. Antes de desativar o plug-in Behaviour - Backward Compatibility 6, sugerimos fazer uma das duas coisas a seguir:

1. Faça isso em um site de desenvolvimento/teste. Dessa forma, se você acidentalmente deixar passar alguma extensão que torne o backend inacessível, isso não fará com que seu site de produção fique indisponível.
2. Certifique-se de ter acesso ao banco de dados. Dessa forma, você poderá ativar novamente o plug-in rapidamente, se necessário. Mais informações abaixo.

### Verificação pré-atualização ou Gerenciar extensões

Teoricamente, a verificação pré-atualização informaria se suas extensões de terceiros são compatíveis com o J6. No entanto, a verificação pré-atualização só é útil se todos os desenvolvedores de extensões tiverem feito com que suas extensões reflitam a compatibilidade. Em um mundo perfeito, a seção **Extensões** da verificação pré-atualização informaria se uma extensão:

* Pode ser atualizada sem o plugin de compatibilidade com versões anteriores ativado
* Pode ser atualizada com o plugin de compatibilidade com versões anteriores ativado
* Se é necessária uma atualização da extensão antes de atualizar do J5 para o J6
* Se uma extensão é completamente incompatível

Os testes mostraram discrepâncias entre extensões que são compatíveis e as que não são. Isso não é um problema do componente de verificação pré-atualização. Em vez disso, os desenvolvedores de extensões enviam, por meio de suas extensões, informações que preencheriam corretamente a verificação pré-atualização. Se suas extensões não estiverem codificadas para informar corretamente esses dados à verificação pré-atualização, há muito pouco (ou nada) que a verificação pré-atualização ou o Projeto Joomla! possam fazer a respeito. Uma boa fonte de informações seria o site do desenvolvedor da extensão de terceiros, para verificar como a extensão específica deve ser tratada durante a atualização do J5 para o J6.

A imagem mais abaixo nesta seção mostra um exemplo do componente de verificação pré-atualização, no Joomla 5.4.x, da seção Extensões.

A seção superior exibirá as extensões que exigem uma atualização. Acesse Sistema -> Atualização -> Extensões e atualize suas extensões.  
A seção intermediária mostra as extensões para as quais não há informações de atualização disponíveis por parte do desenvolvedor da extensão. Você não saberá se elas são compatíveis ou não sem testá-las ou entrar em contato com o desenvolvedor.

A seção inferior mostra as extensões que não exigem atualização. Isso significa que as extensões estão informando ao Joomla que são compatíveis com o Joomla 6. Não é especificado se elas exigem ou não o plugin de compatibilidade com versões anteriores.

Observe que essas extensões não são preferenciais para o Projeto Joomla. Elas são mostradas apenas como exemplo. Foram escolhidas aleatoriamente no JED para fins de teste.

![Seção Extensões da verificação pré-atualização](../../../en/images/migration/joomla-5-to-6-steps/04-steps-5-to-6-pre-update-check.png)

Recomenda-se usar a seção **Extensões** do componente de verificação pré-atualização apenas como uma visão geral de nível extremamente alto, e não como a fonte 100% confiável. Em outras palavras, talvez você não possa confiar no componente de verificação pré-atualização, dependendo das extensões que estiver usando.

*Qual é a fonte confiável, então?* Sistemas -> Gerenciar extensões

![Painel do sistema com Gerenciar extensões destacado](../../../en/images/migration/joomla-5-to-6-steps/05-steps-5-to-6-system-dashboard-manage.png)

Na tela Extensões: Gerenciar, você poderá ver todas as extensões de terceiros que está usando no site. Na captura de tela abaixo, você vê a tela principal. Na coluna Autor, é possível ver o nome de um desenvolvedor popular de extensões em várias linhas. Também é possível ver o Autor do Projeto Joomla em várias linhas.

![Página principal de Gerenciar extensões](../../../en/images/migration/joomla-5-to-6-steps/06-steps-5-to-6-extensions-manage.png)

Verifique suas extensões de terceiros. Em seguida, você precisará determinar se elas são compatíveis com o J6 (com ou sem o plugin de compatibilidade com versões anteriores) ou não. Se não forem, a atualização não será bem-sucedida.

### Três maneiras de verificar a compatibilidade das suas extensões de terceiros com o J6

1. Consulte o site do desenvolvedor.
2. Faça um backup/cópia do seu site J5, restaure-o em um subdomínio, ative o modo de depuração e siga o passo a passo (abaixo) para atualizar para o J6. Verifique se algo apresenta problemas. Se isso acontecer, desative cada extensão que gerar um erro, anotando qual é a extensão. Você precisará entrar em contato com o desenvolvedor sobre isso, pois ela não é compatível com o J6.
3. Instale um pacote limpo do J6 em um subdomínio, ative o plugin Behaviour - Backward Compatibility, instale todas as extensões que você usa e verifique se elas funcionam.

OBSERVAÇÃO: O Diretório de Extensões do Joomla! (JED) exibirá selos de compatibilidade com o Joomla 6 para extensões que sejam compatíveis com ou sem o uso do plugin de compatibilidade retroativa.

Você pode combinar as opções acima. Comece com uma instalação limpa e teste suas extensões. Quando souber quais funcionam ou não, você poderá trabalhar com os desenvolvedores para verificar em que ponto está o desenvolvimento delas para o J6. ENTÃO, quando todas as suas extensões funcionarem em um site limpo, você saberá que pode **testar** uma atualização completa do J5.4.x para o 6.x.

Talvez você queira determinar se uma extensão funciona sem o plugin de compatibilidade retroativa ativado. Nesse caso, você precisará ter acesso ao banco de dados. Planeje-se para isso. Certifique-se de ter acesso ao banco de dados.

Depois de instalar uma nova instalação do J6, o plugin de compatibilidade retroativa estará desativado. Instale cada extensão uma por vez. Se ela derrubar o seu site, ative o plugin de compatibilidade retroativa por meio do banco de dados.

O Plugin de Compatibilidade Retroativa pode ser encontrado no banco de dados, na tabela #__extensions. Ele se chama plg_behaviour_compat6. Defina o campo Enabled como 0 para desativar o plugin e como 1 para ativá-lo. Ao ativar novamente o plugin de compatibilidade retroativa, você poderá recuperar o acesso ao painel administrativo do Joomla (desde que a extensão funcione com o plugin de compatibilidade retroativa).

OU

Você pode desativar extensões individuais no banco de dados para continuar testando suas outras extensões e verificar se elas funcionarão sem o plugin de compatibilidade ativado. Essas entradas estarão na tabela #__extensions. Altere o campo Enabled para 0 para desativar a extensão.

Em alguns casos, quando você instala no J6 uma extensão que não é compatível com ou sem o plugin de compatibilidade retroativa ativado, será necessário localizar no banco de dados as entradas dessa extensão (pode haver poucas ou muitas) e desativá-las até recuperar o acesso ao painel administrativo. Essas entradas estarão na tabela #__extensions. Você deverá alterar o campo Enabled para 0 para desativar a extensão. Assim que conseguir acessar novamente o painel administrativo do Joomla, poderá desinstalá-la corretamente em Sistema -> Gerenciar -> Extensões. Em seguida, entre em contato com o desenvolvedor.

### Cassiopeia e Weblinks

#### Cassiopeia

Cassiopeia continuará sendo o template do frontend do Joomla 6. Suas personalizações devem continuar funcionando, mas recomendamos testá-las em um site de desenvolvimento para garantir.

#### com_weblinks

A extensão Weblinks funciona no J6 sem o plugin de compatibilidade retroativa ativado a partir da versão 5.4.0:

- [Weblinks Evolved in the JCM](https://magazine.joomla.org/all-issues/september-2025/joomla-weblinks-evolved-insights-from-gsoc-2025). 
- [Weblinks on the JED](https://extensions.joomla.org/extension/weblinks/).

### Teste

Como parte do seu planejamento, recomenda-se testar a atualização em um subdomínio ou localmente para determinar se ela funciona perfeitamente. Certifique-se de acompanhar todas as etapas necessárias para que a atualização ocorra **perfeitamente**.

Depois de testar a atualização em um subdomínio ou localhost e verificar que ela funciona **perfeitamente**, você poderá fazer um backup do seu site de produção e realizar a atualização nele. As instruções passo a passo estão abaixo.

## Atualização passo a passo

O site que você atualizará deve atender a todos os requisitos técnicos e estar executando o Joomla 5.4.x para que seja possível atualizá-lo. Se o seu site ainda não estiver executando o Joomla 5.4.x, atualize-o para a versão 5.4.x antes de atualizar para o J6.

1. Siga todas as instruções da seção Planejamento (acima) antes de atualizar.
2. **Faça backup do seu site.**
3. Atualize quaisquer extensões que precisem ser atualizadas.
4. Desative ou desinstale quaisquer extensões que não sejam compatíveis com o J6.
5. Ative o Debug (Configuração Global -> aba Sistema -> configuração Sistema de Debug como Sim).
6. **Faça backup do seu site novamente.**
7. **Teste seu backup para garantir que ele seja restaurado.** (Sim, faça isso. Você se sentirá melhor.)
8. Acesse Sistema -> Atualização -> Joomla
![Painel do sistema com a opção Atualizar Joomla destacada](../../../en/images/migration/joomla-5-to-6-steps/07-steps-5-to-6-system-dashboard-joomla.png)

9. Clique no botão Opções na barra de ferramentas superior, no lado direito.
![Página de atualização do Joomla com o botão Opções destacado](../../../en/images/migration/joomla-5-to-6-steps/08-steps-5-to-6-joomla-update.png)

10. Altere o Canal de atualização para Joomla Next.
![Opções de atualização do Joomla com o canal de atualização destacado](../../../en/images/migration/joomla-5-to-6-steps/09-steps-5-to-6-joomla-update-options.png)

11. Clique em Salvar e fechar na barra de ferramentas superior.
12. Se o seu servidor atender às especificações técnicas, você verá a tela a seguir, com links na barra lateral esquerda para Configurações obrigatórias, Configurações recomendadas e Extensões.
![Verificação pré-atualização com a barra lateral destacada](../../../en/images/migration/joomla-5-to-6-steps/10-steps-5-to-6-pre-update-check-for-6.png)

13. É provável que suas Configurações obrigatórias e Configurações recomendadas estejam corretas, pois esta tela não será exibida se o seu ambiente não atender aos requisitos técnicos. As extensões podem não estar corretas. Consulte a seção Planejamento (acima) sobre a verificação pré-atualização e por que ela pode não apresentar uma marca de seleção verde, mesmo quando todas as extensões são compatíveis. Você já fez seus testes (correto?), então já sabe se elas são compatíveis ou não.
14. O plugin Compatibilidade retroativa 6 está ativado no Joomla 5.4.x. Para atualizar para o J6, o plugin Comportamento - Compatibilidade retroativa precisa ser desativado.
15. **Se você não seguiu as instruções da seção Planejamento (acima) para o teste, pare agora, volte à seção Planejamento e siga as instruções. O planejamento é a parte mais importante desta atualização.**
16. Quando tiver certeza de que todas as suas extensões são compatíveis com o J6 e tiver testado a atualização, obtendo um resultado perfeito, você poderá marcar a caixa para Confirmar os avisos sobre extensões potencialmente incompatíveis e prosseguir com a atualização; clique em OK na caixa pop-up e, em seguida, clique no botão Atualizar.
![Aviso para confirmar os alertas](../../../en/images/migration/joomla-5-to-6-steps/11-steps-5-to-6-pre-update-warnings.png)

17. Em seguida, seu site solicitará novamente que você confirme ter feito um backup (o que você fez e testou para garantir que fosse restaurado).
![Página Carregar e atualizar para o Joomla 6](../../../en/images/migration/joomla-5-to-6-steps/12-steps-5-to-6-upload-and-update.png)

18. Seu site realizará a atualização para o J6.
![Página de progresso da atualização](../../../en/images/migration/joomla-5-to-6-steps/13-steps-5-to-6-joomla-update-progress.png)

19. Uma atualização bem-sucedida exibirá uma tela como esta:
![Página Status da atualização mostrando sucesso](794e27fda1564310c8ac024f2c5b7)

20. Você verá, no canto superior direito da tela, que seu site está usando o Joomla 6.
21. Teste o frontend do seu site.
22. Teste o backend do seu site.
23. Desative o Debug em Sistema -> Configuração Global -> aba Servidor.
24. Corrija sua nova Busca inteligente, se necessário.
25. Desfrute de uma bebida agradável e admire como você é incrível.

## E se algo der errado?

Se você testou tudo antecipadamente, isso não deveria acontecer. Porém, é possível que algo no ambiente tenha mudado ou que algum código de uma extensão tenha sido alterado entre o momento dos testes e a atualização.

Como você ativou o Debug antes de começar, deverá conseguir identificar a extensão que causa o problema e desativá-la (isso talvez precise ser feito no banco de dados caso você não consiga mais acessar o backend para desativá-la). Dessa forma, seu site continuará funcionando enquanto você descobre o que deu errado e corrige o problema.

Na pior das hipóteses, restaure seu backup para ter tempo de investigar o ocorrido em um ambiente de testes.

A opção Correção do banco de dados pode resolver alguns dos seus problemas. Acesse o Painel do sistema e clique em Banco de dados.

![Painel do sistema com o link Banco de dados destacado](../../../en/images/migration/joomla-5-to-6-steps/15-steps-5-to-6-system-dashboard-database.png)

Na página Manutenção: Banco de dados, serão exibidos quaisquer problemas na estrutura do banco de dados que seu site possa ter. Marque a caixa de seleção apropriada e clique no botão Atualizar estrutura na barra de ferramentas superior.

![Página de manutenção do banco de dados mostrando um problema](../../../en/images/migration/joomla-5-to-6-steps/16-steps-5-to-6-maintenance-database.png)

## Outros lugares para obter ajuda

- [Fórum do Joomla: Quadro de Migração e Atualização 6.x](https://forum.joomla.org/viewforum.php?f=866&sid=47959551fb677ee3690f8b61eece277b)
- [Comunidade Joomla no Mattermost](https://joomlacommunity.cloud.mattermost.com/main/channels/town-square)

*Traduzido por openai.com*