<!-- Filename: J4.x:Optional_Technical_Requirements / Display title: Requisitos Técnicos Opcionais -->

Esta página lista os requisitos técnicos *opcionais* que não são necessários para instalar e executar o Joomla!, mas que são necessários para algumas APIs internas. A lista foi criada para o Joomla 4.

| Item                      | Descrição                                                                                                                           |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| **Aplicativo**            |                                                                                                                                     |
| JApplicationDaemon        | Requer as extensões `ext/pcntl` e `ext/posix` do PHP                                                                               |
| **Arquivo**               |                                                                                                                                     |
| BZ2                       | Requer a extensão `ext/bz2` do PHP                                                                                                  |
| GZip                      | Requer a extensão `ext/zlib` do PHP                                                                                                 |
| Zip                       | Requer a extensão `ext/zip` ou `ext/zlib` do PHP                                                                                    |
| **Cache**                 |                                                                                                                                     |
| APC                       | Requer a extensão `ext/apc` do PHP nas versões 5.3 ou 5.4, `ext/apcu` nas versões 5.5 ou 5.6, não suportado no PHP 7.x (Nota: ISSO PRECISA SER VERIFICADO)  |
| APCu                      | Requer a extensão `ext/apcu` do PHP 5.3+                                                                                           |
| CacheLite                 | Requer o pacote PEAR Cache_Lite (testado na versão 1.7.16, funcionará com a 1.8)                                                    |
| Memcache                  | Requer a extensão `ext/memcache` do PHP e um servidor Memcache (Nota: A extensão Memcache não é compatível com PHP 7.x)             |
| Memcached                 | Requer a extensão `ext/memcached` do PHP e um servidor Memcached                                                                    |
| Redis                     | Requer a extensão `ext/redis` do PHP e um servidor Redis                                                                           |
| Wincache                  | Requer a extensão `ext/wincache` do PHP (somente para Windows)                                                                      |
| XCache                    | Requer a extensão `ext/xcache` do PHP                                                                                              |
| **Adaptadores de Cliente**|                                                                                                                                     |
| LDAP                      | Requer a extensão `ext/ldap` do PHP                                                                                                |
| HTTP/Curl                 | Requer a extensão `ext/curl` do PHP                                                                                                |
| HTTP/Socket               | Requer que a função `fsockopen()` do PHP esteja habilitada                                                                         |
| HTTP/Stream               | Requer que a função `fopen()` do PHP e `allow_url_fopen` estejam habilitados                                                       |
| **Criptografia**          |                                                                                                                                     |
| JCrypt                    | Requer a extensão `ext/mcrypt` do PHP para todos os cifradores, exceto o SodiumCipher, que requer `ext/sodium`                     |
| JKeychain                 | Requer a extensão `ext/openssl` do PHP                                                                                             |
| **Banco de Dados**        |                                                                                                                                     |
| Microsoft SQL Azure       | Requer a extensão `ext/sqlsrv` do PHP (a extensão para PHP 5.x apenas suporta Windows; uma versão compatível para Linux está disponível para o PHP 7.x) |
| Microsoft SQL Server      | Requer a extensão `ext/sqlsrv` do PHP (a extensão para PHP 5.x apenas suporta Windows; uma versão compatível para Linux está disponível para o PHP 7.x) |
| MySQL                     | Requer a extensão `ext/mysql` do PHP (não suportado no PHP 7.x)                                                                    |
| MySQLi                    | Requer a extensão `ext/mysqli` do PHP                                                                                              |
| Oracle                    | Requer a extensão `ext/pdo` do PHP com suporte para Oracle (disponível apenas para 3PD; o CMS não funcionará com isso)             |
| PDO MySQL                 | Requer a extensão `ext/pdo` do PHP com suporte para MySQL                                                                          |
| PostgreSQL                | Requer a extensão `ext/pgsql` do PHP                                                                                               |
| SQLite                    | Requer a extensão `ext/pdo` do PHP com suporte para SQLite (disponível apenas para 3PD; o CMS não funcionará com isso)             |
| **Imagem**                |                                                                                                                                     |
|                           | Requer a extensão `ext/gd` do PHP                                                                                                  |
|                           | Requer a extensão `ext/fileinfo` do PHP                                                                                            |
| **Sessão**                |                                                                                                                                     |
| APC                       | Requer a extensão `ext/apc` do PHP nas versões 5.3 ou 5.4, `ext/apcu` nas versões 5.5 ou 5.6, não suportado no PHP 7.x (Nota: ISSO PRECISA SER VERIFICADO)  |
| Memcache                  | Requer a extensão `ext/memcache` do PHP e um servidor Memcache (Nota: A extensão Memcache não é compatível com PHP 7.x)             |
| Memcached                 | Requer a extensão `ext/memcached` do PHP e um servidor Memcached                                                                    |
| Wincache                  | Requer a extensão `ext/wincache` do PHP (somente para Windows)                                                                      |
| XCache                    | Requer a extensão `ext/xcache` do PHP                                                                                              |
| **MELHORIAS OPCIONAIS**   |                                                                                                                                     |
| **String**                |                                                                                                                                     |
| mbstring                  | Habilite a extensão `ext/mbstring` do PHP para que a biblioteca phputf8 utilize funções nativas                                     |

*Traduzido por openai.com*

