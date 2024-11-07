<!-- Filename: Purging_expired_cache_files / Display title: Liberar Cache Expirado -->

## Arquivos de Cache

Arquivos de cache são arquivos temporários criados para melhorar o desempenho do seu site. Você precisa garantir que os arquivos de cache que expiraram, e que portanto não são mais necessários, sejam removidos do sistema. Caso contrário, você eventualmente ficará sem espaço no disco.

Os arquivos de cache expirados podem ser removidos pela interface do Administrador ou pela interface de Linha de Comando (CLI).

## Purge - Método do Administrador

No *Painel Principal*
* Selecione a opção **Cache** no painel do *Sistema*.
* Na página *Manutenção: Limpar Cache*, selecione o botão **Limpar Cache Expirado** na Barra de Ferramentas.

## Purge - Método de Linha de Comando

Abra uma janela de terminal e use o comando cd para navegar até o diretório cli na raiz do seu site.
Se você não souber quais comandos CLI estão disponíveis, execute o seguinte comando:
```bash
php joomla.php
```
Você verá uma lista de comandos disponíveis. O comando `cache` é:
```bash
php joomla.php cache:clean
```
Deve aparecer uma mensagem de confirmação verde ou talvez uma mensagem de erro marrom.  

## Purga Automática de Arquivos de Cache Expirados

Você pode automaticamente purgar arquivos de cache expirados usando um cron job. Serviços de hospedagem facilitam isso ao fornecer um formulário para selecionar com que frequência um trabalho é executado e o comando a ser usado. Então você pode optar por definir o cron para rodar às 05:00 todos os dias com o seguinte comando:
```
/usr/local/bin/ea-php82 /home/username/public_html/cli/joomla.php cache:clean
```
A maioria dos gestores de tarefas *cron* permite que você insira um endereço de e-mail para o qual a saída do cron será enviada. Se você não quiser que uma mensagem seja enviada, adicione ` > /dev/null 2>&1` ao comando.

A versão do PHP usada na linha de comando é frequentemente diferente daquela usada para a entrega de um site. Ela pode ser incompatível com o Joomla. Portanto, use o caminho completo para a versão do PHP que você deseja usar ao invés de `php` apenas.

*Traduzido por openai.com*

