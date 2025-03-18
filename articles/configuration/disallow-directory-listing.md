<!-- Filename: How_do_you_block_directory_scans_using_htaccess%3F / Display title: Desativar Listagem de Diretório  -->

## Contexto

Por padrão, em um servidor web Apache, um diretório que não contém um arquivo de índice configurado (index.html ou index.php) exibirá uma lista de todos os arquivos e subdiretórios no diretório. Isso pode ser útil em um servidor de teste pessoal, mas representa um risco grave de segurança em um servidor de produção ativo.

No passado, era prática comum incluir um arquivo index.html vazio em todos os diretórios do Joomla para evitar esse problema em servidores mal configurados. Isso não é mais necessário. Espera-se uma configuração adequada do servidor, seja nos arquivos de configuração do servidor ou em arquivos .htaccess individuais. O primeiro é preferido, pois é aplicado a todos os sites no servidor.

No entanto, sites em um ambiente de hospedagem compartilhada podem esperar que cada site modifique a configuração do servidor usando arquivos .htaccess. O servidor deve estar configurado para "AllowOverride Options" ou "AllowOverride All" para permitir substituições em .htaccess.

## Usando .htaccess

O arquivo htaccess.txt fornecido com o Joomla pode ser usado em servidores Apache renomeando-o ou copiando-o para .htaccess. Ele contém várias configurações para combater ataques de hackers em sites Joomla. Entre outras, você verá as seguintes configurações para prevenir listagens de diretórios:

```
Options -Indexes

## Sem listagem de diretórios
<IfModule mod_autoindex.c>
    IndexIgnore *
</IfModule>
```

## Teste seu site

Uma maneira de testar seu site é inserir a URL da sua pasta de imagens na barra de URL do navegador: `https://seudominio.com/imagens/`. Como a pasta de imagens normalmente não contém um arquivo index.html ou index.php, você deve ver uma página completamente vazia. Se você vir uma lista de todos os arquivos e pastas, então você não está impedindo varreduras de diretórios em nenhuma parte do seu site. Corrija isso!

*Traduzido por openai.com*
