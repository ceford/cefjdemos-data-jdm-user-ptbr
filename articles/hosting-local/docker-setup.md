<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Configura\u00e7\u00e3o do Docker",
    "description": " ",
    "author": ""
}
-->

## Configurando um ambiente Joomla local usando Docker

Para executar o Joomla no seu computador, são necessárias quatro coisas: 
- baixar e configurar um servidor web **Apache** ou **nginx**, 
- um serviço de banco de dados como **MySQL ou** **MariaDB**, 
- e, certamente, precisamos do **PHP** 
- e do **Joomla.** 

Para fazer com que todas essas partes diferentes se comuniquem entre si, a maioria de nós utiliza softwares integrados como **XAMPP**, **Laragon** ou **FlyEnv**.

No entanto, as configurações tradicionais podem facilmente causar conflitos de porta ou servidores de banco de dados que misteriosamente se recusam a iniciar. Quando um servidor local trava, você pode acabar baixando e reinstalando manualmente sites Joomla inteiros repetidamente só para testar um único PR, possivelmente perdendo seu trabalho enquanto corrige um bug. Isso consome um tempo valioso, e as correções geralmente são apenas soluções temporárias.

**A mudança para o Docker ([Saiba mais sobre o Docker](https://docs.docker.com/get-started/))** 
Com o Docker, você pode
ignorar completamente a configuração manual. Em vez de instalar servidores web diretamente no seu computador, basta escrever um único arquivo de "receita". O Docker baixa, isola e conecta tudo automaticamente em segundo plano. Se algo der errado, você não reinstala toda a sua configuração; simplesmente reinicia o contêiner.

Neste guia, você aprenderá a maneira mais simples de executar um ambiente Joomla local usando o Docker, permitindo que você passe menos tempo corrigindo servidores e mais tempo contribuindo.

### Pré-requisitos

Você só precisa ter uma coisa instalada antes de começarmos: **Docker Desktop**.

- Baixe-o em [**docker.com**](https://www.docker.com/) e execute o
  instalador
- No Windows, deixe marcada a opção "Use WSL 2 instead of Hyper-V" -
  ela torna tudo mais rápido
- Abra o Docker Desktop e aguarde até que o canto inferior esquerdo mostre o status
  verde **Engine running**.

![Docker Desktop](../../../en/images/hosting-local/docker-setup/01-docker-setup-desktop.png)

É só isso.

### O arquivo docker-compose.yml

Quando você precisa que vários serviços se comuniquem — como um servidor web
(Apache/Nginx), PHP e um banco de dados (MySQL/MariaDB) — você usa um arquivo especial
de orquestração chamado `docker-compose.yml`. Esse arquivo funciona como a
planta do seu projeto, definindo todos os serviços necessários e como eles colaboram. (A imagem oficial do Docker para Joomla é, na verdade, baseada em uma imagem de PHP e Apache. Isso significa que, usando apenas essa imagem do Joomla, você obtém PHP, Apache e Joomla integrados).

Primeiro, crie uma nova pasta no seu computador para o seu projeto (por
exemplo, na sua Área de Trabalho, crie uma pasta chamada `joomla-docker`).

Dentro dessa pasta, crie um novo arquivo de texto e dê a ele exatamente este nome:

    docker-compose.yml

Abra esse arquivo em qualquer editor de texto (como o VS Code ou o Notepad), cole o
código a seguir exatamente como está e salve-o:

```
    services:
      joomla:
        image: joomla:latest
        ports:
          - "8080:80"
        environment:
          - JOOMLA_DB_HOST=db
          - JOOMLA_DB_USER=joomla
          - JOOMLA_DB_PASSWORD=joomlapass
          - JOOMLA_DB_NAME=joomladb
        depends_on:
          - db
      db:
        image: mariadb:10.11
        environment:
          - MYSQL_ROOT_PASSWORD=rootpass
          - MYSQL_DATABASE=joomladb
          - MYSQL_USER=joomla
          - MYSQL_PASSWORD=joomlapass
        volumes:
          - db_data:/var/lib/mysql
    volumes:
      db_data:
```

### Iniciando o ambiente

Abra seu terminal (ou o PowerShell no Windows), navegue até a pasta `joomla-docker`
e execute:

```
    docker compose up -d
```

Na primeira vez que você executar esse comando, o Docker baixará as imagens do Joomla e do MariaDB, o que pode levar um ou dois minutos, dependendo da velocidade da sua internet. Depois disso, cada inicialização subsequente será quase instantânea, como você pode ver abaixo.

![Saída de inicialização do Docker no terminal](../../../en/images/hosting-local/docker-setup/02-docker-setup-terminal-transcript.png)

### O instalador do Joomla

Abra seu navegador e acesse `http://localhost:8080`. Você deverá ver a
tela de instalação do Joomla.

![Configuração do instalador do Joomla — Nome do site](../../../en/images/hosting-local/docker-setup/03-docker-setup-joomla-installer-sitename.png)

Preencha o nome do seu site e os dados do administrador na primeira tela.

![Dados de login do instalador do Joomla](../../../en/images/hosting-local/docker-setup/04-docker-setup-joomla-installer-login-data.png)

Ao chegar à tela de **Configuração do banco de dados**, é aqui que a maioria
das pessoas fica presa:

**Não digite `localhost` como nome do host.**

Como o banco de dados está sendo executado em seu próprio contêiner, o Joomla precisa do
nome do serviço do contêiner — não de localhost. Use estes valores exatos:

- **Tipo de banco de dados:** MySQLi
- **Nome do host:** `db`
- **Nome de usuário:** `joomla`
- **Senha:** `joomlapass`
- **Nome do banco de dados:** `joomladb`

![Configuração do banco de dados do instalador do Joomla](../../../en/images/hosting-local/docker-setup/05-docker-setup-joomla-installer-database-config.png)

Clique nas etapas seguintes, conclua a instalação e pronto.

Quando terminar de trabalhar no dia, execute `docker compose stop` para
pausar os contêineres e liberar memória. Na próxima vez, seu site estará exatamente
onde você o deixou.

------------------------------------------------------------------------

### Problemas comuns

- **A página em localhost:8080 não carrega logo após a inicialização:** O
  contêiner do banco de dados leva alguns segundos para concluir a inicialização. Aguarde 30
  segundos e atualize a página.
- **A porta 8080 já está em uso:** Altere `"8080:80"` para `"8081:80"` no
  arquivo compose e acesse o site em `localhost:8081`.
- **Os contêineres foram iniciados, mas o Joomla exibe um erro de banco de dados:** Verifique novamente
  se o Nome do host no instalador é `db` e não `localhost`.

### Dica profissional: acessando os arquivos do Joomla para desenvolvimento

No momento, seu site Joomla está em execução, mas os arquivos PHP reais estão
ocultos dentro do contêiner do Docker. Se você quiser contribuir com o Joomla,
testar PRs ou escrever seus próprios plugins, precisará desses arquivos no seu
computador para poder abri-los no VS Code ou em seu editor favorito.

Para sincronizar os arquivos do contêiner com o disco rígido local, basta
adicionar duas linhas (`volumes: `) e (`- ./site_joomla:/var/www/html`)
à seção `joomla` do seu arquivo `docker-compose.yml`, conforme mostrado abaixo:

```yml
services:
  joomla:
    image: joomla:latest
    ports:
      - "8080:80"
    volumes:
      - ./site_joomla:/var/www/html
    # ... (rest of your settings)
```

**O que isso faz:** 

Na próxima vez que você executar `docker compose up -d`, o Docker criará
automaticamente uma pasta chamada `site_joomla` ao lado do seu arquivo de
composição. Ele copiará todo o núcleo do Joomla (incluindo o painel
administrativo, os componentes e os templates) para essa pasta.

![Explorador do IDE com a instalação do Joomla no Docker](../../../en/images/hosting-local/docker-setup/06-docker-setup-ide-explorer.png)

Quaisquer alterações no código feitas nessa pasta em seu computador serão
atualizadas instantaneamente dentro do contêiner em execução! Agora você está
totalmente preparado para o desenvolvimento local.

### Dica bônus 1: testando versões específicas do Joomla e do PHP

Ao testar PRs, os mantenedores frequentemente pedirão que você teste com
versões específicas do PHP. Com o XAMPP, fazer downgrade ou upgrade do PHP é um
pesadelo. Com o Docker, isso leva dois segundos.

Em vez de usar `image: `**`joomla:latest`** no seu
**`docker-compose.yml`**, você pode especificar versões exatas usando tags. Por
exemplo, se precisar testar o **Joomla 5.2** no **PHP 8.3**, basta alterar essa
linha para: **`image: joomla:5.2-php8.3-apache`**

Execute **`docker compose up -d`** novamente, e o Docker substituirá
instantaneamente o ambiente do seu servidor. Você pode encontrar todas as tags
de versão disponíveis na <a href="https://hub.docker.com/_/joomla" class="ng-star-inserted"
target="_blank" rel="noopener" data-hveid="0"
data-ved="0CAAQ_4QMahgKEwjl8vi347CTAxUAAAAAHQAAAAAQkgI">página oficial do Joomla
no Docker Hub</a>.

### Dica bônus 2: adicionando o phpMyAdmin

Se você vem do **XAMPP**, talvez sinta falta de ter uma interface visual para
consultar seu banco de dados. Você pode adicionar facilmente o **phpMyAdmin** à
sua configuração adicionando um novo **bloco de serviço** ao final do seu
arquivo **`docker-compose.yml`**:

```yml
    phpmyadmin:
        image: phpmyadmin/phpmyadmin:latest
        ports:
          - "8081:80"
        environment:
          - PMA_HOST=db
        depends_on:
          - db
```

Reinicie seus contêineres e agora você poderá acessar o phpMyAdmin acessando
**http://localhost:8081** no navegador. Basta fazer login usando **`joomla`**
como nome de usuário e **`joomlapass`** como senha.

*Traduzido por openai.com*

