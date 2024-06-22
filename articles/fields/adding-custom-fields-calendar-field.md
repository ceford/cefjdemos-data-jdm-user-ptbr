<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Adicionando campos customizados/Campo Calendário -->

<span id="section-portal-heading"></span>

## Campo Calendário

**Articles in this Series**

1.  Introduction
2.   Parameters for all Custom
    Fields
3.   Calendar
    Field
4.   Checkboxes
    Field
5.   Color
    Field
6.   Editor
    Field
7.   Integer
    Field
8.   List
    Field
9.   List of Images
    Field
10.  Media
    Field
11.  Radio
    Field
12.  Repeatable
    Field
13.  Sql
    Field
14.  Text
    Field
15.  Textarea
    Field
16.  Url
    Field
17.  User
    Field
18.  Usergroup
    Field
19.  How can you group custom
    fields
20.  What components are supporting custom
    fields
21.  Implementation into your
    component
22.  Use custom fields in your
    overrides

## Campo Calendário

Fornece uma caixa de texto para a entrada de uma data. Um ícone ao lado
da caixa de texto linka para um calendário pop-up, que também pode ser
usado para inserir o valor da data.

#### Opções

Se você usar a data padrãoː o valor pode ser um formato ISO 8601
(AAAA-MM-DD HH: MM: SS) ou NOW, que exibe a data atual. **Cuidado**:
Mesmo que você não especifique a hora na data padrão, a hora é exibida
quando a opção *Mostrar hora* estiver ativada.
As opções especiais dentro deste campo são:

- Mostrar hora
  Se ativado, o campo do calendário também exibirá a hora. Os formatos
  são localizados usando as cadeias de linguagem regulares.

#### Informações relacionadas

Veja:

-  Campo de formulário tipo
  Calendário
- <a href="http://php.net/manual/en/datetime.formats.date.php"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Formatos de data</a>

#### Prints de tela

##### Criando o campo

Digamos que você crie um campo com as opções mostradas na próxima
figura.

<img
src="https://docs.joomla.org/images/thumb/5/55/Calendar_field_create-en.png/670px-Calendar_field_create-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/5/55/Calendar_field_create-en.png/1005px-Calendar_field_create-en.png 1.5x, https://docs.joomla.org/images/5/55/Calendar_field_create-en.png 2x"
data-file-width="1291" data-file-height="663" width="670" height="344"
alt="Calendar field create-en.png" />

##### Usando o campo no backend

No backend, ao criar um artigo ou um contato, você vê o campo como na
seguinte imagemː

<img
src="https://docs.joomla.org/images/thumb/f/f9/Calendar-en.png/670px-Calendar-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/f/f9/Calendar-en.png/1005px-Calendar-en.png 1.5x, https://docs.joomla.org/images/f/f9/Calendar-en.png 2x"
data-file-width="1291" data-file-height="663" width="670" height="344"
alt="Calendar-en.png" />

##### Usando o campo no frontend

No frontend, você pode ver o campo como na seguinte imagem. A opção
*Exibição automática* é responsável pela posição do campo e seu modelo
(template) é responsável pelo design do campo.
Os campos apenas são exibidos no *frontend* se você os tiver preenchido
com dados no artigo. Se não for um campo obrigatório, você pode
esquecer?

<img
src="https://docs.joomla.org/images/thumb/f/fb/Calendar_field_frontend-en.png/670px-Calendar_field_frontend-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/f/fb/Calendar_field_frontend-en.png/1005px-Calendar_field_frontend-en.png 1.5x, https://docs.joomla.org/images/f/fb/Calendar_field_frontend-en.png 2x"
data-file-width="1291" data-file-height="663" width="670" height="344"
alt="Calendar field frontend-en.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields"
id="content-button" class="button expand success">Ant: Parâmetros para
todos os Campos Customizados</a> <a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Checkboxes_Field"
id="content-button" class="button expand">Prox: Campo Checkbox</a>
