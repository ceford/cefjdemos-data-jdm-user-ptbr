<!-- Filename: J4.x:Language_Overrides / Display title: Substituições de Idioma  -->

## Localizações dos Arquivos de Idioma

A maioria dos arquivos de idioma do Joomla! estão localizados em pastas de idioma, uma na raiz do site e outra na pasta do administrador. Cada idioma possui sua própria subpasta baseada nos códigos de idioma padrão RFC3066. Cada extensão armazena suas traduções com um nome derivado do nome da extensão. Alguns exemplos:

    siteroot/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.sys.ini

Os arquivos contêm linhas consistindo em uma chave e sua tradução:

    COM_CONTENT="Artigos"
    COM_CONTENT_ADD_NEW_MENU_ITEM="Novo Item de Menu"
    COM_CONTENT_ARTICLE_CONTENT="Conteúdo"
    COM_CONTENT_ARTICLES_TABLE_CAPTION="Tabela de Artigos"
    COM_CONTENT_ARTICLES_TITLE="Artigos"

O código PHP do Joomla usa a chave. Ela é substituída pela tradução do texto em tempo de execução. O arquivo .ini contém traduções usadas pela extensão. Os arquivos sys.ini contêm traduções usadas pelo Joomla para gerenciar a extensão. Pode haver centenas de linhas em um arquivo de idioma.

Aconselha-se que extensões de terceiros armazenem seus arquivos de idioma em pastas de idioma dentro da extensão. Lá, eles estão seguros de serem deletados caso um administrador decida desinstalar um idioma. Exemplo:

    siteroot/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.sys.ini

**Nunca edite nenhum arquivo de idioma central do Joomla! ou de terceiros! Quaisquer alterações que você fizer serão perdidas na próxima atualização. Se você deseja alterar as palavras de qualquer item de idioma, use o componente formal de Substituição de Idioma.**

As sobrecargas de idioma são suas substituições para traduções de chaves de idioma centrais ou de extensão. Estas são traduções individuais, uma ou duas, não um arquivo inteiro! As substituições de idioma para um determinado idioma são todas armazenadas em um arquivo:

    siteroot/language/overrides/en-GB.override.ini
    siteroot/language/overrides/fr-FR.override.ini
    siteroot/language/overrides/de-DE.override.ini

    siteroot/administrator/language/overrides/en-GB.override.ini
    siteroot/administrator/language/overrides/fr-FR.override.ini
    siteroot/administrator/language/overrides/de-DE.override.ini

### Ordem de Carregamento de Idioma

A cada carregamento de página, as traduções do idioma en-GB são carregadas primeiro. Isso garante que nenhuma chave seja vista pelos usuários do site. Se outro idioma estiver em uso, as traduções para esse idioma são carregadas a seguir, substituindo as traduções de en-GB. Outros idiomas tendem a ficar atrás do en-GB na criação de traduções, então os usuários podem ocasionalmente ver palavras ou frases em inglês entre aquelas do seu próprio idioma.

Por fim, as traduções são carregadas a partir do arquivo de substituição de idioma. Isso permite que o site use palavras ou frases alternativas para atender a circunstâncias locais.

## Substituições de Idioma

Ocasionalmente, você pode desejar substituir um único item de idioma traduzido por algo mais adequado às circunstâncias locais. Um caso comum é quando você cria uma substituição de modelo ou layout e deseja adicionar algum conteúdo que utilize uma nova chave de idioma. O exemplo a seguir ilustra um caso em que algum texto foi adicionado ao layout de logout do módulo de login, descrito no artigo sobre Layouts de Modelo. O layout alternativo tem este código:

```html
<p class="text-center">
Sua sessão expirará em <br><?php echo $endTime; ?>
</p>
```

Para um site multilíngue usando inglês, francês e alemão, o código precisa mudar:

```html
<p class="text-center">
<?php echo Text::_('TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT')?><br><?php echo $endTime; ?>
</p>
```

Nota: se você seguiu o tutorial de Layout de Modelo, pode já ter uma chave TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES que traduz como Expira. Mas isso é usado em siteroot/administrator/language/overrides.

A nova chave agora pode ser traduzida para cada idioma. As traduções serão salvas em siteroot/language/overrides.

- Selecione **Sistema** → **Painel de Gerenciamento** → **Substituições de Idioma**
- Selecione seu idioma e a localização do Site.
- Selecione o botão **Novo** e preencha o formulário. Neste exemplo, a chave de idioma é **TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT** e o texto pode ser **Sua sessão expirará em**
- Salve & Feche o formulário.
- Repita o processo de tradução para cada idioma.

![formulário de substituição de idioma editar](../../../en/images/languages/language-overrides-edit.png)

Finalmente, verifique se a tradução foi implementada.

![Resultado da Substituição no formulário de login do site](../../../en/images/languages/language-overrides-custom-logout.png)

*Traduzido por openai.com*

