<!-- Filename: jdocmanual?manual=user&heading=help&filename=administrator-help.md / Display title: Ajuda do Administrador -->

## Introdução

Quase todas as páginas do Administrador do Joomla têm uma Barra de Ferramentas com um botão de **Ajuda** próximo ao canto superior direito da página. Somente os Painéis não possuem uma Barra de Ferramentas e, portanto, um botão de Ajuda.

Muitas páginas também possuem um botão rotulado como **Alternar Ajuda Inline**. Este simplesmente exibe ou oculta a descrição de um campo, se disponível. Seu propósito é reduzir a desordem, mas fornecer um mecanismo de lembrete onde isso seria útil. Não é abordado aqui em mais detalhes.

O botão **Ajuda** aciona a abertura de uma nova janela usando uma URL embutida no botão. Um exemplo:
```
data-url="https://help.joomla.org/proxy/index.php?keyref=Help51:Articles&lang=en"
```
Neste caso, o conteúdo da página de Ajuda vem de uma fonte externa.

## A Fonte de Ajuda - um site MediaWiki

MediaWiki é o software usado pela Wikipédia. É um pacote de Software Livre e de Código Aberto (FOSS) que usa PHP e MySQL, assim como o Joomla. Você pode baixá-lo e instalá-lo por conta própria. Em teoria, você poderia criar seu próprio servidor de ajuda e usá-lo em vez do servidor de ajuda comunitário do Joomla. Na prática, você precisa saber que as páginas do MediaWiki necessitam de algum processamento para torná-las adequadas para exibição como páginas de ajuda. 

É aí que entra o **proxy**. Ele busca a página necessária da instalação do MediaWiki e a prepara para exibição como uma página de ajuda. Você pode ver uma página original do MediaWiki neste exemplo em https://docs.joomla.org/Help5.x:Articles e pode editá-la se encontrar algo errado. 

## A URL Global de Ajuda

O arquivo **configuration.php** na raiz de uma instalação do Joomla contém uma variável `$helpurl`:

```
$helpurl = 'https://help.joomla.org/proxy/index.php?keyref=Help{major}{minor}:{keyref}&lang={langcode}';
```

Quando um botão de Ajuda é selecionado, cada um dos itens entre chaves é substituído. Os valores {major} e {minor} são as configurações de versão para sua instalação. O {langcode} é o código do idioma atualmente selecionado para o Administrador, que pode ser en, de ou fr.

A variável {keyref} é o nome do arquivo de uma página no servidor de Ajuda, sem o seu namespace. Portanto, para a página de Artigos, o nome de arquivo relevante é *Articles*.

**Nota:** `https://docs.joomla.org/` é o site para editar páginas de Ajuda. Mas `https://help.joomla.org/proxy` é o site para recuperar páginas de Ajuda.

Não há provisão para mudar a URL padrão do servidor de Ajuda a partir dos formulários de Configuração Global do Administrador, mas você pode alterá-la com um editor de texto.

A lista completa dos códigos de substituição disponíveis é:

| Código         | Será substituído por                                                                   |
|----------------|----------------------------------------------------------------------------------------|
| {app}          | Nome da aplicação (ex.: "Administrator" no back-end do Joomla CMS)                    |
| {component}    | Nome do componente (ex.: "com_content" no Gerenciador de Artigos)                      |
| {keyref}       | Referência da chave da tela de Ajuda (após passar pelo sistema de tradução)            |
| {major}        | Número de revisão principal do Joomla (ex.: "5" no Joomla 5.6).                        |
| {minor}        | Número de revisão secundária do Joomla (ex.: "1" no Joomla 5.1)                        |
| {maintenance}  | Número de revisão de manutenção do Joomla (ex.: "3" no Joomla 5.1.1).                  |
| {language}     | Código completo do idioma (ex.: "en-GB")                                               |
| {langcode}     | Parte da etiqueta de idioma do código de idioma (ex.: "en" se o código completo é "en-GB") |
| {langregion}   | Parte da etiqueta de região do código de idioma (ex.: "GB" se o código completo é "en-GB")   |

## Ajuda Global no Futuro

O uso de um site MediaWiki para a entrega de páginas de ajuda é um certo
ônus para aqueles que mantêm a documentação e o procedimento pode mudar no
futuro. Se houver uma mudança, é provável que a origem consistirá em
arquivos HTML pré-construídos acessados com uma simples alteração do domínio de origem $helpurl.

## Ajuda Local de Componente Personalizado

Se você tem um componente personalizado e está confortável em editar código fonte PHP e criar conteúdo, pode criar suas próprias páginas de ajuda individuais. Tome o componente Jdocmanual como exemplo. Como um componente personalizado, não há páginas de ajuda no site docs.joomla.org MediaWiki. Componentes de terceiros não têm permissão para ter páginas de ajuda hospedadas lá.

Dê uma olhada neste fragmento de código em administrator/components/com_jdocmanual/src/View/Manual/ViewHtml.php:
```
        $tmpl = $app->input->getCmd('tmpl');
        if ($tmpl !== 'component') {
            ToolbarHelper::help('jdocmanual', true);
        }
```
A especificação da chamada ToolbarHelper::help é a seguinte:
```
@param $ref: O nome do arquivo de destino (excluindo a extensão do arquivo).
@param $useComponent: Use o arquivo de ajuda no diretório do componente.
@param $url: Use este URL em vez de qualquer outro.
@param $component: Nome do componente para obter ajuda (nulo para o componente atual)
function Toolbar::help(
    string $ref,
    bool $useComponent = false,
    string $url = null,
    string $component = null
): HelpButton
Escreve um botão de ajuda para uma determinada opção (abre uma janela popup).
```
Neste exemplo, **$ref** é um nome de arquivo a ser usado, neste caso `'jdocmanual'` (deve corresponder ao caso do arquivo de destino) e **$useComponent** é `true`, o que significa que a página de ajuda a ser usada estará localizada dentro dos arquivos do componente em administrator/component/com_jdocmanual/help/en-GB/jdocmanual.html

Usar um arquivo de ajuda dentro do componente deve significar que a ajuda nunca está ausente e talvez sempre atualizada.

## Ajuda Remota para Componente Personalizado

Na criação do botão de Ajuda, você pode definir `$useComponent = false` e definir a URL para apontar para um local específico no seu próprio site ou em um site remoto.

```
    ToolbarHelper::help('jdocmanual', false, 'http://example.com/help/pt-BR/jdocmanual.html');
```

Assim, tudo o que é necessário é uma página HTML com o nome correto no local correto.

*Traduzido por openai.com*

