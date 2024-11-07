<!-- Filename: J4.x:Apache_PHP_Handler / Display title: Manipuladores Apache PHP -->

## Notas

Para determinar qual método seu servidor web está usando para lidar com arquivos PHP, use os links **Administrador / Sistema / Informações do Sistema** e selecione a aba Informações do PHP. Procure na página por **Server API**. As maneiras comuns de um servidor Apache lidar com arquivos PHP incluem o seguinte:

### DSO (mod_php)

- **Vantagem:** um dos manipuladores mais rápidos disponíveis.
- **Desvantagem:** funciona apenas com uma única versão do PHP; arquivos salvos por scripts PHP são de propriedade do usuário Apache **exceto** quando usados em conjunto com mod_ruid2.
- **Para reconhecer:** Server API - Apache 2.0 Handler

### CGI/FastCGI

- **Vantagem:** scripts executam como o usuário do domínio ou subdomínio, manipulador muito rápido.
- **Desvantagem:** mais lento que mod_php, não é possível colocar alterações de configuração do PHP em um arquivo .htaccess.
- **Para reconhecer:** Server API - CGI/FastCGI

### FPM/FastCGI

- **Vantagem:** muito rápido, nível adicional de flexibilidade.
- **Desvantagem:** utiliza mais memória que a maioria dos outros, não é possível colocar alterações de configuração do PHP em um arquivo .htaccess.
- **Para reconhecer:** Server API - FPM/FastCGI

### LSAPI (mod_lsapi)

- **Vantagens:**
   - Oferece suporte para cache.
   - É o manipulador mais performático com baixo consumo de memória.
   - Não é necessária configuração.
   - Pode trabalhar com múltiplas versões do PHP em uma única configuração.
   - Suporta diretivas de configuração do PHP por meio de arquivos .htaccess.
   - Seguro porque os scripts são executados como o proprietário do domínio.
- **Desvantagens:**
   - Não disponibiliza todas as capacidades do LSAPI.
- **Para reconhecer:** Server API - ?

Em um laptop ou desktop local, você pode usar mod_php, mas pode ser necessário definir o usuário do Apache para seu próprio nome de usuário e apontar o diretório raiz do documento para um local no seu próprio espaço de arquivos. Caso contrário, você terá problemas de permissões de arquivos e pastas.

Em um serviço de hospedagem, você precisa usar uma das alternativas FastCGI ou LSAPI. Os serviços de hospedagem podem dar a você uma escolha.

*Translated by openai.com*

