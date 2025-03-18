<!-- Filename: J5.x:Improving_SEO_with_Strict_Routing_and_SEF_URLs / Display title: SEO Roteamento Estrito -->

## Introdução

A opção de Roteamento Estrito, introduzida no Joomla 5.2, melhora o desempenho de SEO da plataforma ao permitir regras de roteamento mais rigorosas usando uma alternância no plugin *System - SEF*. Isso ajuda a eliminar conteúdo duplicado, aplicando URLs mais consistentes e redirecionando duplicatas para a URL correta com um redirecionamento 301.

![system sef plugin settings](../../../en/images/seo/seo-system-sef-plugin.png)

### Aplicação de Sufixos

Atualmente, o Joomla permite acesso a URLs com ou sem sufixo quando esta opção está ativada nas opções de *Configuração Global*.

A opção **Impor um sufixo por redirecionamento** no plugin *Sistema - SEF* aplica um comportamento consistente de sufixo. Quando ativada, ela redireciona solicitações GET para uma URL com um sufixo, caso esteja ausente. Também redirecionará URLs com um parâmetro de formato de consulta para a URL mais limpa, substituindo o sufixo pelo parâmetro de formato quando necessário.

Esta funcionalidade deve se tornar o comportamento padrão no Joomla 6.0, onde a opção de ativá-la ou desativá-la será removida, e essa funcionalidade será integrada ao sistema de roteamento principal. Por enquanto, esta opção permite que os usuários testem o comportamento em sistemas ao vivo e a desativem caso surjam problemas imprevistos durante o período de transição do Joomla 5.1 para o 6.0.

## Como Acessar

Para ativar o roteamento restrito para SEO:

1. Selecione o item **Plugins** no *Painel Inicial*.
2. Encontre e abra o plugin **System - SEF**.
3. Defina **Strict Routing** como *Sim* para habilitar um tratamento mais rigoroso de URLs.
4. Defina **Enforce a Suffix by Redirect** como Sim ou Não, dependendo de sua preferência para impor sufixos de URL.

Uma vez ativado, o Joomla redirecionará automaticamente os URLs duplicados para o correto com um redirecionamento 301, melhorando o SEO ao consolidar o conteúdo em um único URL autoritativo.

## Notas Adicionais

Esta funcionalidade foi projetada para funcionar como uma etapa preparatória para futuras melhorias de SEO e é ativada automaticamente para novas instalações do Joomla 5.2. Ela estabelece as bases para futuros aprimoramentos no sistema de roteamento do Joomla.  
*Traduzido por openai.com*

