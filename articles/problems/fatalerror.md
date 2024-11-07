<!-- Filename: J4.x:FatalError / Display title: ErroFatal -->

## Introdução

De tempos em tempos, o Joomla pode exibir uma página de erro em vez da página que você esperava. Existem dois tipos de páginas de erro:

- A página de erro do sistema tem um fundo vermelho. É acionada se houver um erro sério antes que o modelo do site ou do administrador seja processado.
- A página de erro do modelo se parece com o modelo normal do site ou do administrador, mas a área de conteúdo é substituída por uma mensagem de erro. Isso é acionado quando o erro ocorre no código de conteúdo.

### Página de Erro do Sistema

![Página de erro fatal do sistema](../../../en/images/problems/fatal-error.png)

### Página de Erro do Modelo

![Página de erro do modelo](../../../en/images/problems/template-error.png)

## Como Resolver

Existem várias razões possíveis para que erros fatais ocorram. Aqui estão apenas algumas:

- Uma mudança no seu host, por exemplo, uma versão do PHP atualizada que não é compatível com o Joomla ou uma das suas Extensões.
- Um problema com espaço em disco, uso de memória ou tempo limite de script.
- Uma Extensão recém-instalada ou ativada que não é compatível com o Joomla. Um plugin ruim pode desativar o login do Administrador!

### Ativar Debug

Se a sua interface de Administrador **ainda estiver** funcionando:
- Vá para **Painel Inicial → Painel do Sistema → Configuração Global**. 
- Na aba Sistema, defina *Sistema de Depuração* como *Sim*.
- Na aba Servidor, defina *Relatório de Erros* como *Máximo*.
- Então, *Salve & Feche*.

Se a sua interface de Administrador **não estiver** funcionando, edite o arquivo *configuration.php* na pasta raiz do seu site Joomla.

1. Mude as permissões de *444* ou *-r--r--r--* (ninguém tem permissão para escrever no arquivo) para *644* ou *-rw-r--r--* (apenas o Proprietário tem permissão para escrever).
2. Edite o arquivo com um editor de texto e defina `$debug` para `true` e `$error_reporting` para `'maximum'`.
3. *Salve* o arquivo.

Com as alterações feitas, recarregue a página que estava causando o erro. Agora você deve ver uma rastreabilidade de pilha. Exemplo:

![Página de erro do template](../../../en/images/problems/template-error-stack-trace.png)

O primeiro item na rastreabilidade de pilha indica onde o erro foi disparado. Às vezes, isso é suficiente para identificar a Extensão defeituosa. Outras vezes, a Extensão defeituosa está mais abaixo na rastreabilidade de pilha. Pode não significar muito para você, mas a rastreabilidade de pilha é inestimável para os especialistas que respondem perguntas nos Fóruns do Joomla.

Se você conseguir identificar a Extensão defeituosa, desative-a. Você pode fazer isso usando a interface de Administrador se ela estiver funcionando. Caso contrário, use o phpMyAdmin para encontrar a Extensão na tabela de banco de dados `#__extensions` e defina o valor `enabled` como `0`. Você não deve precisar desativar nenhuma Extensão central do Joomla.

## Assistente de Postagem do Fórum

Para ajudar a resolver problemas, você deve baixar o
[Assistente de Postagem do Fórum (FPA)](https://forumpostassistant.github.io/docs/) e
carregá-lo na raiz do seu site Joomla. O link para encontrá-lo também está
próximo ao topo de cada página do Fórum Joomla. O FPA é um script PHP
independente que analisa a sua instalação do Joomla e informa o que pode
estar errado. Novamente, isso pode não significar muito para você, mas os
especialistas que respondem perguntas nos Fóruns podem pedir para vê-lo.

## Fazendo Limpeza

Quando o seu problema for resolvido:

1. Vá para **Início do Dashboard → Painel do Sistema → Configuração Global**
2. Selecione a aba Sistema e defina *Debug do Sistema* como *Não*.
3. Selecione a aba Servidor e defina *Relatório de Erros* como *Padrão do Sistema*.
4. *Salvar & Fechar*.
5. Remova o Assistente de Postagens do Fórum.

As permissões do `configuration.php` são definidas como somente leitura (444 ou *r--r--r--*) 
quando o formulário de Configuração Global é salvo. Não é necessário fazê-lo manualmente.

*Traduzido por openai.com*  

