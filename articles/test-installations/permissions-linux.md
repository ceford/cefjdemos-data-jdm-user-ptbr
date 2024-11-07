<!-- Filename: Verifying_permissions / Display title: Permissões de Arquivo: Linux -->

## Introdução

As informações a seguir são para servidores baseados em Linux. Se o seu servidor web for um servidor baseado em Microsoft Windows (IIS), você deve consultar [Permissões: Windows](jdocmanual?article=user/test-installations/permissions-windows).

Dependendo da configuração de segurança do seu servidor web, as permissões padrão recomendadas são:

- 755 para diretórios
- 644 para arquivos
- 444 para o arquivo `configuration.php` (quando uma alteração na Configuração Global é
  salva, o Joomla primeiro altera a permissão para 644, salva a alteração e depois
  altera a permissão de volta para 444)

<div class="alert alert-warning">
Atenção!

Nunca use 777 a menos que você saiba o que está fazendo! Não use extensões que 
exijam permissões 777!
</div>

## Como Localizar as Permissões

Existem vários métodos disponíveis para visualizar e alterar as permissões de arquivos ou pastas de sites. O navegador de arquivos do painel de controle do host ou um programa comum de [Protocolo de Transferência de Arquivos (FTP)](https://pt.wikipedia.org/wiki/File_Transfer_Protocol) devem fornecer um método para ver e alterar permissões de arquivos e pastas. A linha de comando é boa para aqueles que têm acesso ao terminal e estão familiarizados com comandos do sistema.

Dependendo do que você está usando, você deve ver algo como esta imagem de parte do sistema de arquivos raiz do Joomla visto no cPanel:

![verificando permissões no cpanel](../../../en/images/test-installations/verifying-permissions-cpanel.png)

As permissões estão mais à direita e são precedidas por um zero para indicar que são números octais. Deve haver um formulário para alterar as permissões de um ou mais itens selecionados:

![alterando permissões no cpanel](../../../en/images/test-installations/verifying-permissions-cpanel-change.png)

Em uma janela de terminal, as permissões de arquivos e pastas são exibidas como grupos de letras em vez de números (o `d` inicial indica que o item é um diretório):

```sh
drwxr-xr-x   20 ceford  staff     640 14 Oct 22:23 components
-r--r--r--    1 ceford  staff    3485 27 Oct 06:56 configuration.php
drwxr-xr-x    2 ceford  staff      64 20 Oct 14:21 files
-rw-r--r--    1 ceford  staff    6899 30 Sep 09:27 htaccess.txt
drwxr-xr-x   15 ceford  staff     480 24 Oct 12:19 images
```

## Números de Permissão

Em uma exibição de permissões no formato 777, cada dígito octal corresponde a 
três letras para três grupos de usuários diferentes:

- Primeiro dígito = proprietário (o proprietário do item - `ceford` na lista da linha de comando acima)
- Segundo dígito = grupo (o grupo com acesso permitido - `staff` na lista acima)
- Terceiro dígito = outros (todos os demais neste computador)

## Significado dos números

Cada dígito octal é a soma das permissões concedidas:
```sh
     r = Ler     = 4
     w = Escrever = 2
     x = Executar = 1
```
Some os números para cada permissão necessária para um determinado grupo de usuários:

| "Octal" \# | (r)ler | (w)escrever | e(x)ecutar | Usuário ou Grupo ou Outros |
|------------|--------|-------------|------------|----------------------------|
| 0          | não    | não         | não        | `---` 0+0+0 = 0            |
| 1          | não    | não         | sim        | `--x` 0+0+1 = 1            |
| 2          | não    | sim         | não        | `-w-` 0+2+0 = 2            |
| 3          | não    | sim         | sim        | `-wx` 0+2+1 = 3            |
| 4          | sim    | não         | não        | `r--` 4+0+0 = 4            |
| 5          | sim    | não         | sim        | `r-x` 4+0+1 = 5            |
| 6          | sim    | sim         | não        | `rw-` 4+2+0 = 6            |
| 7          | sim    | sim         | sim        | `rwx` 4+2+1 = 7            |


## Exemplos

- 755 é rwx (proprietário), r-x (grupo) e r-x (outros) ou, em outras palavras, todos podem ler e executar, mas apenas o proprietário (você) pode fazer alterações no arquivo. Ficaria assim quando tudo estiver junto: `-rwxr-xr-x`. Esta é a configuração normal para pastas.
- 644 é rw-, r--, r-- ou todos podem ler o arquivo, mas apenas o proprietário pode escrever no arquivo ou `-rw-r--r--`. Esta é a configuração normal para arquivos.
- 777 ou `-rwxrwxrwx` significa que TODOS podem ler, escrever e executar QUALQUER arquivo
  <div class="alert alert-warning">
  Isso é algo que você **NUNCA** deve permitir no seu servidor/site, a menos que tenha certeza absoluta do que está fazendo.
  </div>

As permissões são usadas tanto para diretórios quanto para arquivos, e é por isso que você pode ver isto `drwxr-xr-x`, onde o `d` é de diretório.

Para uma explicação completa, leia o artigo da Wikipedia sobre 
[Permissões de sistema de arquivos](https://en.wikipedia.org/wiki/Filesystem_permissions)

*Traduzido por openai.com*

