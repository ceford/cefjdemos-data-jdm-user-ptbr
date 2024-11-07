<!-- Filename: Debugging_a_translation / Display title: Depurando uma Tradução   -->

## Arquivos de Idioma Joomla

Sempre que um texto precisa ser exibido na tela, os programadores do Joomla inserem uma constante de idioma, como JYES ou JNO. Durante o processo de renderização, arquivos de idioma são carregados com traduções no idioma apropriado. Os arquivos de idioma terminam com `.ini`. Você pode consultar languages/en-GB/joomla.ini para alguns exemplos básicos. Linhas que começam com um ponto e vírgula são ignoradas e podem ser usadas para comentários. As linhas restantes consistem em pares de chave="valor". Cada idioma tem o mesmo conjunto de chaves, mas os valores são as traduções apropriadas.

Cada extensão do Joomla tem seus próprios arquivos de idioma, portanto, existem centenas deles no total. Às vezes, ocorrem problemas como a ausência de constantes de idioma, constantes de idioma com erro de ortografia ou erros de sintaxe nas strings de tradução que podem invalidar um arquivo de idioma inteiro.

## Depuração de Idioma

O Joomla fornece alguns mecanismos de depuração úteis que podem facilitar a localização de strings não traduzidas e diagnosticar problemas com traduções de idiomas em extensões instaladas. Para experimentar:

No Painel Inicial:

* Selecione o botão **Configuração Global** no painel *Sistema*.
* Selecione o painel *Sistema* e defina **Depuração de Idioma** como **Sim**.
* **Exibição de idioma** geralmente está configurada para **Valor**. Se configurada para **Constante**, o layout é interrompido por constantes longas que não quebram.

Com a Depuração de Idioma ativa, todos os valores traduzíveis são mostrados cercados por caracteres especiais que indicam seu status:

* `**Joomla CMS**` Texto cercado por dois asteriscos indica que uma correspondência foi encontrada em um arquivo de idioma e a constante foi traduzida.
* `??Joomla CMS??` Texto cercado por pares de pontos de interrogação indica que a constante é traduzível, mas nenhuma correspondência foi encontrada em um arquivo de idioma.
* `Joomla CMS` Texto sem caracteres circundantes indica que o valor não é traduzível.

## Depurar Sistema

Informações adicionais de depuração de idioma podem ser obtidas ativando a depuração do sistema.

A partir do Painel Inicial:

* Selecione **Plugins** e, em seguida, encontre e ative o plugin **System - Debug**.
* Selecione o Painel Inicial novamente e...
* Selecione o botão **Configuração Global**.
* Selecione o painel *Sistema* e defina **Depurar Sistema** como **Sim**.

Com a **Depuração do Sistema** ativa, todas as telas apresentam informações adicionais de depuração na parte inferior de cada página. Pode ser expandida a partir de um ícone do Joomla, e a borda superior pode ser arrastada verticalmente para mostrar mais linhas.

As informações de depuração são divididas em vários tópicos:

* **J! Info** Informações básicas de instalação.
* **Request** Campos de solicitação do servidor.
* **Session** Informações da sessão
* **Profile** O tempo gasto para executar o código até vários pontos de marcação no código.
* **Queries** As consultas SQL executadas no processo de construção da página.
* **Loaded.** Uma lista de todos os arquivos de idioma carregados no processo de construção da página, incluindo informações do caminho completo. Isso pode ser útil para verificar se os arquivos esperados foram carregados.
* **Untranslated** Uma lista de todas as constantes não traduzidas encontradas e a provável localização do arquivo dado onde foi feita a chamada de tradução.
* **Errors**

## Sistema - Plugin de Depuração

Este plugin do sistema controla o que é exibido quando o modo de depuração é ativado na **Configuração Global**. Há três configurações de interesse para tradutores.

Na aba **Idioma**:

![plugin do sistema de depuração](../../../en/images/languages/languages-debug-plugin.png "Sistema - Depuração de Idioma")

* **Erros Ao Analisar Arquivos de Idioma** Exibe um erro se um arquivo de idioma falhar ao carregar.

- **Arquivos de Idioma**. Se definido como *Mostrar*, então...
- **String de Idioma** Se definido como *Mostrar*, então...
- **Remover Primeira Palavra**.
- **Remover Do Início**
_ **Remover Do Fim**

**A seguinte explicação precisa de revisão!**

Note que strings não traduzidas só exibirão o valor passado para o método **Text** apropriado. Por exemplo, com o seguinte código:

```php
echo Text::_('Reports Import Configuration');
```

Se não traduzido, exibirá como:

```plaintext
# /administrator/components/com_reports/views/reports/tmpl/default.php
REPORTS IMPORT CONFIGURATION=Reports Import Configuration
```

Se o Prefixo da Chave Removido for definido como "Reports", então a exibição mudaria ligeiramente para:

```plaintext
# /administrator/components/com_reports/views/reports/tmpl/default.php
REPORTS IMPORT CONFIGURATION=Import Configuration
```

Note que o caminho mostrado é apenas uma melhor suposição baseada em uma chamada à função PHP *debug_backtrace*. Às vezes é preciso, às vezes não é, e há também casos em que nenhum arquivo pode ser determinado. Nesses casos, você deve usar seu melhor julgamento.

*Traduzido por openai.com*

