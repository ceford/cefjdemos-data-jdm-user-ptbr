<!-- Filename: Get_locally_hosted_Joomla!_website_e-mail_functions_to_work / Display title: Email do Host Local -->

## Hospedagem Local

A maioria dos provedores de internet bloqueia a porta 25, então você não pode enviar e-mails do servidor SMTP do seu próprio computador. Isso é feito para bloquear spammers. Se você não pretende enviar spam, pode usar o servidor de e-mail do seu provedor.

Para usar a função de e-mail do servidor SMTP do seu provedor de internet, mesmo que esteja hospedando seu próprio site Joomla no seu próprio computador, faça login no seu site Joomla como Super Usuário e navegue até a aba **Servidor** na página de **Configuração Global**. Na seção de **E-mail**, seus dados devem parecer com o seguinte:

    Do Email: alguem@example.com (geralmente você)
    Do Nome: AlgumNome

    Mailer: SMTP
    Host SMTP: smtp.charter.net (O que seu provedor te informa para usar nos servidores SMTP deles)
    Caminho Sendmail: /usr/sbin/sendmail
    Porta SMTP: 25
    Segurança SMTP: STARTTLS
    Autenticação SMTP: Sim (ou Não)
    Nome de Usuário SMTP: johndoe (nome de usuário de uma das suas contas de e-mail no seu provedor)
    Senha SMTP: trr33459 (senha de uma das suas contas de e-mail no seu provedor)

Envie uma mensagem de teste para verificar se está funcionando.

O Nome de Usuário SMTP, Senha e Host são os mesmos campos que você preenche ao adicionar uma Conta no Outlook Express, Eudora ou qualquer cliente de e-mail que você possa usar no seu computador.

Você pode ter problemas com extensões que alteram o endereço *De* nos e-mails enviados. Por exemplo, a extensão ProjectFork às vezes envia e-mails como se fossem da pessoa responsável pelo projeto. Isso pode causar um problema porque alguns servidores SMTP de provedores não permitem um endereço "de" que não corresponde ao nome de usuário (por exemplo, Rogers no Canadá). Você receberá uma mensagem como esta: "PHPMAILER_FROM_FAILEDname@whatever.com." Uma solução é garantir que você sempre use um endereço de e-mail válido do seu provedor para seus usuários.

*Traduzido por openai.com*

