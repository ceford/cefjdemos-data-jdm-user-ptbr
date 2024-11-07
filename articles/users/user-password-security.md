<!-- Filename: J5.x:Enhancing_Password_Security_with_Symbolic_Characters / Display title: Segurança da Senha do Usuário  -->

## Introdução

Na aba *Opções de Senha* do formulário *Usuários: Opções*, os valores mínimos para *Números*, *Símbolos*, *Letras Maiúsculas* e *Letras Minúsculas* estão todos definidos como 0 por padrão. Para uma melhor segurança, esses valores devem ser definidos como 1. Senhas novas ou alteradas devem então incluir um de cada um desses caracteres.

## Símbolos

O *Open Worldwide Application Security Project* (OWASP) recomenda que todos os 
caracteres especiais disponíveis em um teclado padrão dos EUA sejam reconhecidos e 
aceitos ao definir requisitos de senha.

```
 !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
 ```

Não é óbvio, mas esta lista inclui o caractere de espaço.

[OWASP: Caracteres Especiais de Senha](https://owasp.org/www-community/password-special-characters)

Antes da versão 5.2, esses símbolos podiam ser usados em senhas, mas alguns deles
não eram reconhecidos como símbolos para fins de validação de senha:
```
@[]£^+±~<>/'",.
``` 

*Traduzido por openai.com*

