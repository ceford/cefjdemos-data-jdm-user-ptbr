<!-- Filename: J4.x:Fix_%22Database_Table_Structure_NOT_Up_to_Date%22_before_Update / Display title: Estrutura da Tabela do Banco de Dados -->

## Erros Relatados

Ao atualizar o Joomla!, a estrutura da tabela do banco de dados precisa estar atualizada antes que o processo possa começar. A *Verificação Pré-Atualização para Joomla* reclamará se não for esse o caso.

No entanto, quando você vai para **Sistema → Manutenção → Banco de Dados**, não há nenhuma entrada disponível. Isso foi relatado em várias versões do Joomla! 4.x.

## Qual é a Causa

O problema é causado por uma tabela `#__schemas` vazia no banco de dados. Muito
provavelmente, isso ocorre quando a instância do Joomla! não é instalada pelo
instalador oficial do Joomla!, mas por meio de um script personalizado que não
preencheu todos os dados necessários.

## Como Corrigir

Você pode corrigir isso adicionando o valor ausente à tabela. Usando o phpMyAdmin (ou outro cliente de banco de dados), vá para a tabela `#__extensions`. Procure por `name='files_joomla'` e anote o `extension_id` (no nosso caso *211*).

Em seguida, você precisa saber qual é o script SQL mais recente que está instalado. Vá para `administrator/components/com_admin/sql/updates/mysql` e pegue o nome do arquivo com a versão mais alta. Neste exemplo, assuma que *4.0.3-2021-09-05.sql* é o nome do arquivo com a versão mais alta. Agora você precisa adicionar isso na sua consulta de inserção como o segundo valor:

```sql
INSERT INTO `#__schemas` (`extension_id`, `version_id`) VALUES (211, '4.0.3-2021-09-05');
```

ou para PostgreSQL:

```sql
INSERT INTO "#__schemas" ("extension_id", "version_id") VALUES (211, '4.0.3-2021-09-05');
```

Substitua `#__` pelo prefixo do seu banco de dados antes de executar as instruções.

Em seguida, no menu do Administrador, vá para **Sistema → Manutenção → Banco de Dados** e corrija as tabelas.

Agora a atualização deve funcionar como esperado.

*Traduzido por openai.com*

