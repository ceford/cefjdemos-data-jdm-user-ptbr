<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Campo num\u00e9rico",
    "description": " ",
    "author": ""
}
-->

## Objetivo

O campo numérico fornece um método para inserir um número real com a opção de anexar uma moeda ou outro símbolo antes ou depois do número. O controle pode ser usado como um campo inteiro com setas de incremento e decremento, com um intervalo padrão de 1 a 100. No entanto, valores reais, positivos ou negativos, podem ser inseridos no campo. Exemplo: `99.99` poderia ser formatado para aparecer como `£99.99` para o usuário final. Ou `-273.15` poderia aparecer como `-273.15C` para o usuário final.

## Criação do campo

### Aba Geral

![Criação do campo numérico](../../../en/images/fields/adding-custom-fields-number-field/01-fields-number-edit.png)

- **Tipo** Número, que não pode ser alterado após a seleção.
- **Nome** O nome exclusivo do campo.
- **Rótulo** Um rótulo traduzível para o campo.
- **Descrição** Uma descrição opcional e traduzível do campo.
- **Obrigatório** Defina como *Sim* se este campo for obrigatório?
- **Usar somente em subformulário** *Sim* ou *Não*.
- **Valor padrão** Um valor padrão opcional.
- **Mínimo** O valor mínimo que pode ser escolhido usando as setas para cima/baixo; o padrão é 1. Pode ser um número negativo, portanto, defina-o como menor que o número mais baixo esperado, **caso contrário, selecionar a seta para baixo poderá apagar o número existente**.
- **Máximo** O valor máximo que pode ser escolhido usando as setas para cima/baixo; o padrão é 100. Defina-o como maior que o número mais alto esperado, **caso contrário, selecionar a seta para cima poderá apagar o número existente**.
- **Incremento** O tamanho do incremento adicionado ou subtraído do valor atual do campo usando as setas para cima/baixo. Pode ser um número inteiro, cujo padrão é 1, ou um decimal, como 0.01. **Defina-o como a menor quantidade pela qual você deseja incrementar ou decrementar o valor**.
- **Formatar como moeda** Se selecionado, haverá campos adicionais:
    - **Símbolo da moeda** Pode ser um único símbolo, como `£` ou `$`, ou uma cadeia de caracteres, como `&deg;C`, que aparece como *&deg;C*.
    - **Posição do símbolo** Selecione *Antes* ou *Depois* do número.
    - **Número de casas decimais** Normalmente 2 para moedas, mas pode ser diferente em outros contextos.

### Aba Opções

#### Painel Opções do formulário:

- **Texto de espaço reservado** Texto de espaço reservado que aparecerá dentro do campo como uma dica para o usuário sobre a entrada necessária.
- **Classe do campo** Uma classe opcional adicionada ao campo do formulário de entrada de dados.
- **Classe do rótulo** Uma classe opcional adicionada ao rótulo do campo.
- **Editável em** Interfaces de edição permitidas: *Site*, *Administrador* ou *Ambos*. 
- **Atributo Showon** Mostra ou oculta condicionalmente o campo dependendo do valor de outros campos. 

#### Painel Opções de exibição:

- **Classe de exibição** A classe do contêiner do campo na saída.
- **Classe do valor** A classe do valor do campo na saída.
- **Rótulo** *Mostrar* ou *Ocultar* o rótulo na saída. Se definido como Mostrar:
    - **Classe do rótulo (saída)** Uma classe para o rótulo na saída.
- **Exibição automática** Se e onde o campo deve ser exibido:
    - **Após o título**
    - **Antes do conteúdo exibido**
    - **Após o conteúdo exibido**
    - **Não exibir automaticamente**
- **Prefixo** Texto que aparecerá antes do valor do campo.
- **Sufixo** Texto que aparecerá depois do valor do campo.
- **Layout** uma lista de layouts disponíveis.
- **Exibir quando somente leitura** Escolha entre *Herdar*, *Sim* ou *Não*.

#### Painel Pesquisa inteligente

- **Índice de pesquisa** Escolha entre pesquisar ou não e o método de pesquisa.

### Abas Publicação e Permissões

O conteúdo dessas abas é autoexplicativo e é abordado em outra parte.

## Entrada de dados

Entrada de dados: basta digitar o valor desejado. Este exemplo é o ponto de ebulição do argônio:

![Entrada de dados do campo numérico](../../../en/images/fields/adding-custom-fields-number-field/02-fields-number-data-entry.png)

**Atenção:** se o número inserido estiver fora do intervalo mínimo e máximo definido nas opções de criação do campo, um rótulo flutuante do navegador informará isso, mas as informações fornecidas não serão aplicadas. Você pode inserir um número fora do intervalo, e ele será aceito.

## Exibição de dados

A imagem a seguir mostra a exibição de um item com um valor negativo:

![Exibição do campo numérico no site](../../../en/images/fields/adding-custom-fields-number-field/03-fields-number-site.png)

*Traduzido por openai.com*