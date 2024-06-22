<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Hiawatha / Display title: Habilitando URLs amigáveis para mecanismos de buscas (SEF) no Hiawatha -->

Use a seguinte regra do UrlToolkit para habilitar URLs limpos no
servidor web Hiawatha:

    UrlToolkit {
        ToolkitID = joomla
        Match base64_encode.*\(.*\) DenyAccess
        Match (<|%3C).*script.*(>|%3E) DenyAccess
        Match GLOBALS(=|\[|\%[0-9A-Z]{0,2}) DenyAccess
        Match _REQUEST(=|\[|\%[0-9A-Z]{0,2}) DenyAccess
        RequestURI exists Return
        Match /index.php Return
        Match ^/component/ Skip 2
        Match ^(/|\.php|\.html|\.htm|\.feed|\.pdf|\.raw|/[^.]*)$ Skip 1
        Skip 1
        Match .* Rewrite /index.php
    }

Habilite uma regra do UrlToolkit para um host virtual por meio da
configuração do UseToolkit:

    VirtualHost {
        ...
        UseToolkit = joomla
    }
