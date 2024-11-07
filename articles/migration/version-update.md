<!-- Filename: J4.x:Updating_from_an_existing_version / Display title: Atualização de Versão -->

## Introdução

**Lembre-se: Sempre faça backup do seu site antes de atualizar.**

A maneira recomendada de atualizar instalações do Joomla! é usar o *Componente de Atualização do Joomla*.

Uma instalação padrão do Joomla 4 e versões posteriores inclui um painel de notificações útil no Painel Inicial após o login. Você pode ver rapidamente se uma atualização está disponível e o número da versão.

A mensagem de atualização que aparece no painel de Notificações depende do *Canal de Atualização* configurado na página *Opções de Atualização do Joomla* e da versão *Menor* atual. Com o **Canal de Atualização** definido como **Padrão**, as atualizações dentro da versão *Maior* atual são notificadas. Com o parâmetro definido como *Joomla Next*, você pode atualizar para a versão atual mais recente e, em seguida, selecionar o botão **Verificar Atualizações** para ver se a próxima versão *Maior* está disponível.

Embora o Joomla o notifique quando uma atualização estiver disponível, é necessário que você execute a atualização. É um processo simples que deve ser realizado na primeira oportunidade para manter o site atualizado.

## Acessando o Componente de Atualização

Se o painel de notificações estiver exibido no Painel Inicial, selecione o botão **x.y.z Disponível - Atualize Agora!** para ir ao Componente de Atualização.

![notificação de atualização do joomla no painel inicial](../../../en/images/migration/version-update-notification-home-dashboard.png)

Alternativamente, para acessar o Componente de Atualização a partir do menu do Administrador, selecione **Sistema** para ir através do **Painel do Sistema**.

![notificação de atualização do joomla no painel do sistema](../../../en/images/migration/version-update-notification-system-dashboard.png)

O Painel do Sistema possui um *Painel de Atualização* que inclui um link do Joomla que mostrará o número da versão disponível para atualização. Selecione o link **Joomla** para ir ao Componente de Atualização.

## Realizando a Atualização

O Joomla! 4 e 5 fornecem uma Verificação Pré-Atualização para Atualizações de Versões Menores. Esta visão do componente de Atualização do Joomla mostra especificações técnicas do servidor em que o site está hospedado e extensões do núcleo e de terceiros que utilizam o Servidor de Atualizações em formato de lista.

**Nota:** A tela de *Verificação Pré-Atualização* não é exibida se o site estiver na versão **Menor** atual.

![verificação pré-atualização joomla](../../../en/images/migration/version-update-pre-update-check.png)

Preste muita atenção aos resultados da verificação e tome medidas para corrigir quaisquer problemas destacados antes de atualizar. Pode ser necessário atualizar, desativar ou desinstalar extensões incompatíveis antes de atualizar o Joomla.

Não é incomum ver avisos para *Configurações Recomendadas*, pois estes geralmente são específicos do servidor e relacionados à hospedagem. Provavelmente, eles já existiam quando você instalou o Joomla e, muito provavelmente, não impedirão a conclusão da atualização.

*Observe o lembrete de que é fortemente aconselhado fazer um backup, se ainda não tiver feito!*

Há um link abaixo do botão de atualização. Na maioria dos casos, você pode ignorar este link. Ele oferece uma opção para carregar manualmente os arquivos de atualização se o seu servidor estiver atrás de um firewall ou não puder contatar os servidores de atualização do Joomla.

Quando você tiver revisado a Verificação Pré-Atualização e estiver satisfeito, selecione **Atualizar**.

### Confirmando a Atualização

![página de início da atualização](../../../en/images/migration/version-update-start-update.png)

Clique na caixa de seleção para confirmar que você fez um backup e verificou que as extensões são compatíveis, em seguida, clique em **Iniciar Atualização**.

### Progresso da Atualização

![página de progresso da atualização](../../../en/images/migration/version-update-progress.png)

Assim que a atualização começar, uma barra de progresso aparecerá à medida que os arquivos do Joomla forem atualizados.

### Conclusão

![página de conclusão da atualização](../../../en/images/migration/version-update-completion.png)

Quando a barra de progresso alcançar 100%, uma mensagem do sistema confirmará que seu site foi atualizado, assim como o número da versão. O número da versão também será atualizado na barra de ferramentas superior, ao lado do nome do site.

Clique no botão **Voltar** e você será retornado ao Componente de Atualização do Joomla, onde é possível verificar novamente se há atualizações.

## Verificações após Atualização

Assim que a atualização for concluída, você deve realizar algumas verificações para garantir que tudo ocorreu como esperado, que não há erros presentes e que não houve alterações que exijam ações adicionais.

### Verificação do Frontend

Vá para o frontend do site e verifique se ele está funcionando e exibindo como antes da atualização. Use a combinação *Shift + Recarregar* para forçar seu navegador a recarregar quaisquer alterações em folhas de estilo e scripts.

### Verificações do Sistema

No menu lateral, selecione **Sistema** para ir para o Painel de Controle do Sistema. Isso oferece uma visão geral do status atual do seu site Joomla.

![painel de controle do sistema após atualização](../../../en/images/migration/version-update-after-update.png)

Neste exemplo, podemos ver que desde a atualização temos dois itens que requerem atenção. Eles são marcados com um rótulo que inclui um número. O número se refere a quantos itens requerem atenção. Clicar em cada um permitirá que você os corrija.

**Nota** O Painel de Controle do Sistema faz uma verificação cada vez que a página é carregada. Lembre-se de que as configurações de cache do navegador podem afetar isso. É uma boa prática limpar o cache do navegador ao verificar usando *Shift + Recarregar*.

### Verificação do Banco de Dados

Navegue até **Sistema → Manutenção → Banco de Dados**. Se seu banco de dados estiver atualizado, você deverá ver uma tela semelhante à abaixo:

![verificação de banco de dados pós-atualização sem problemas](../../../en/images/migration/version-update-after-update-database-check-no-problems.png)

Se seu banco de dados não estiver atualizado, você verá uma tela listando os problemas encontrados, semelhante à abaixo:

![verificação de banco de dados pós-atualização com problemas](../../../en/images/migration/version-update-after-update-database-check-problems.png)

Neste caso, selecione o *Nome* da extensão problemática e, em seguida, o botão Atualizar Estrutura na Barra de Ferramentas. O Joomla atualizará seu banco de dados para corrigir os problemas listados e então reexibirá a tela. Se a correção for bem-sucedida, a exibição indicará que o banco de dados está atualizado.

**Nota:** Se ainda existirem erros, certifique-se de que todas as tabelas do banco de dados estejam verificadas.

## Descobrir Sistema

Em alguns casos, quando você atualiza para uma nova versão do Joomla, novas extensões do núcleo são adicionadas. Se houveram problemas com a atualização do banco de dados, essas extensões podem não ter sido instaladas corretamente. Para verificar isso, navegue até **Sistema → Descobrir**. Em seguida, selecione o ícone Descobrir na barra de ferramentas. A tela deve ser exibida da seguinte forma:

![Tela de Descoberta Sem Extensões Para Instalar](../../../en/images/migration/version-update-after-update-discover.png)

Se for assim, você sabe que quaisquer novas extensões adicionadas durante a atualização foram instaladas corretamente no banco de dados.

Se houver extensões não instaladas, elas aparecerão de forma semelhante à seguinte tela:

![Tela de Descoberta Com Extensões Descobertas Para Instalar](../../../en/images/migration/version-update-after-update-discover-found.png)

Nesse caso, marque as caixas e clique no ícone Instalar na barra de ferramentas. O Joomla instalará a(s) extensão(ões) e, em seguida, exibirá a tela mostrando que nenhuma extensão foi descoberta. Nesse ponto, as novas extensões foram instaladas no banco de dados.

## Solução de Problemas

Se você tiver alguma dúvida, problema ou erro antes, durante ou após a
atualização, por favor, faça suas perguntas no
[Fórum de Migração e Atualização para Joomla! 4.x](https://forum.joomla.org/viewforum.php?f=812).

Se você encontrar problemas ou erros durante o processo de atualização, aqui estão algumas
dicas.

- Limpar o cache do seu navegador. Pode ter havido mudanças no CSS ou
  Javascript que precisarão ser recarregadas pelo seu navegador da Web após uma
  atualização.
- Se alguma mensagem de erro do banco de dados aparecer após a atualização, verifique
  o link **Sistema → Painel de Manutenção → Banco de Dados**. Em alguns
  casos, se ocorrer um erro de banco de dados, isso impedirá que todas as
  atualizações do banco de dados sejam executadas. Nesse caso, você pode executá-las a partir do link do Banco
  de Dados e, em seguida, usar o método **Sistema → Instalar → Descobrir** para verificar e instalar quaisquer novas extensões.
- O processo de atualização cria ou adiciona a um arquivo de log chamado
administrator/logs/joomla_update.php, que você pode abrir com um editor de texto para
ver as etapas registradas no log. Ele mostrará as etapas principais (baixar zip,
instalar, executar comandos SQL, limpeza), algo assim:

```
2024-04-17T09:13:16+00:00	INFO 127.0.0.1	update	Atualização iniciada pelo usuário Jimmy (139). A versão antiga é 5.0.3.
2024-04-17T09:13:18+00:00	INFO 127.0.0.1	update	Baixando o arquivo de atualização de ...
2024-04-17T09:13:28+00:00	INFO 127.0.0.1	update	Arquivo Joomla_5.1.0-Stable-Update_Package.zip baixado.
2024-04-17T09:13:28+00:00	INFO 127.0.0.1	update	Iniciando a instalação da nova versão.
2024-04-17T09:13:40+00:00	INFO 127.0.0.1	update	Finalizando a instalação.
2024-04-17T09:13:40+00:00	INFO 127.0.0.1	update	Início das atualizações de SQL.
2024-04-17T09:13:40+00:00	INFO 127.0.0.1	update	A versão atual do banco de dados (esquema) é 5.0.0-2023-09-11.
... Várias consultas SQL individuais
2024-04-17T09:13:41+00:00	INFO 127.0.0.1	update	Fim das atualizações de SQL.
2024-04-17T09:13:41+00:00	INFO 127.0.0.1	update	Desinstalando extensões
2024-04-17T09:13:41+00:00	INFO 127.0.0.1	update	Excluindo arquivos e pastas removidos.
2024-04-17T09:13:44+00:00	INFO 127.0.0.1	update	Limpando após a instalação.
2024-04-17T09:13:44+00:00	INFO 127.0.0.1	update	A atualização para a versão 5.1.0 está completa.
```

*Traduzido por openai.com*

