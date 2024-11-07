<!-- Filename: J4.x:Article_Check-out_and_Check-in / Display title: Artigo: Check-in  -->

## Introdução

Muitos sites Joomla têm vários usuários com permissão para editar artigos. Para evitar que dois usuários tentem editar o mesmo artigo ao mesmo tempo, cada artigo possui um campo de banco de dados **checked_out** para indicar se ele está ou não em uso. Esse campo é definido quando um artigo é aberto para edição e desmarcado quando o formulário de edição é fechado usando os botões *Salvar e Fechar* ou *Fechar*.

Às vezes, um formulário de edição de artigo não é fechado corretamente, por exemplo, ao usar o botão voltar do navegador ou quando a sessão do usuário expira. Nesse caso, o campo checked_out permanece definido. Isso é marcado nas listas de artigos com um pequeno ícone de cadeado. O ícone de cadeado também é visto onde um link de edição deveria estar quando se está logado no frontend do site.

Para restaurar o funcionamento normal, os itens marcados como checked out precisam ser liberados.  

## Check-in do Artigo

Existem vários métodos disponíveis para fazer o check-in de um artigo.

- Se você foi a última pessoa a editar o artigo, poderá editá-lo a partir do backend ou frontend sem a necessidade de fazer o check-in.
- Entre em contato com a última pessoa que editou o artigo para verificar se ela terminou. Você pode passar o cursor sobre o cadeado, e o tooltip exibirá o nome do usuário que fez o check-out do artigo.
- Se você for um Super Usuário ou Administrador, pode selecionar o ícone do cadeado para fazer o check-in desse item.
- Você também pode selecionar vários artigos e usar o item *Check-in* no botão *Ações* na barra de ferramentas.
- Se você não puder fazer o check-in do item, peça a um Super Usuário ou Administrador que o faça.

## Check-in Global

Se você é um Super Usuário ou Administrador, pode usar a ferramenta de Check-in Global para selecionar itens a serem marcados como verificados.

Esta ferramenta deve ser usada com muito cuidado, especialmente em ambientes de múltiplos usuários. Ela marca como verificados todos os itens anteriormente alocados, independentemente de terem sido alocados por você ou não. Possíveis efeitos colaterais indesejáveis podem ocorrer, como múltiplos editores trabalhando no mesmo documento. Neste caso, a versão de quem clicar no botão salvar por último será salva como cópia final.

Você também deve estar ciente de que muitas outras extensões possuem campos **checked_out**. Por exemplo, módulos e categorias podem ser alocados para edição e serem deixados acidentalmente nesse estado.

No menu do Administrador:

- Selecione **Painel Principal → Check-in Global** ou
  **Sistema → Painel de Manutenção → Check-in Global**.
- A lista mostra o número de itens alocados.

![Página de check-in global](../../../en/images/articles/global-checkin.png)

- Na lista de tabelas do banco de dados, selecione a caixa de seleção para o tipo de item a ser verificado.
- Selecione *Check-in* na Barra de Ferramentas.

Todos os itens alocados nessa tabela serão marcados como verificados.

## Tabelas com o campo checked_out

Você pode descobrir quais tabelas têm uma coluna checked_out com esta consulta usada no phpMyAdmin:

```sql
SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('checked_out') AND TABLE_SCHEMA='j423sd';
```

E o resultado deve ser assim:

```plaintext
TABLE_NAME
bi2hb_banner_clients
bi2hb_banners
bi2hb_categories
bi2hb_contact_details
bi2hb_content
bi2hb_extensions
bi2hb_fields
bi2hb_fields_groups
bi2hb_finder_filters
bi2hb_menu
bi2hb_modules
bi2hb_newsfeeds
bi2hb_scheduler_tasks
bi2hb_tags
bi2hb_update_sites
bi2hb_user_notes
bi2hb_workflow_stages
bi2hb_workflow_transitions
bi2hb_workflows
```

*Tradução por openai.com*

