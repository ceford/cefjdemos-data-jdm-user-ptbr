<!-- Filename: Backup_Basics_for_a_Joomla!_Web_Site / Display title: Básico de Cópias de Segurança para um site em Joomla! -->

Guarde sempre uma cópia de segurança do seu site. Problemas acontecem,
mas existem vários motivos para se ter a cópia a mão antes que surja
algum necessidade.

Existem várias causas para perda de dados. Um site em Joomla pode sofrer
ataques caso o administrador não tenha dado muita atenção a segurança
ou, em alguns casos em que hackers ataquem. Joomla! foi projeto para
trabalhos em grupo e até mesmo um bom editor pode errar e danificar o
site.

Existem diversas situações que o administrador do site precise recuperar
uma cópia funcional do site.

Pratique criar a cópia e restaurá-la. Não espere por uma emergência para
saber como proceder da melhor maneira. Por não saber, pode-se criar uma
cópia vazia ou corrompida, para depois descobrir que nenhum dado
importante foi realmente guardado. Treine e se familiarize com os
procedimentos e ferramentas usadas no processo.

Guardar uma cópia vai além da segurança contra acidentes, pois o hábito
ajuda a criar novos recursos de proteção. Fazer a cópia e restaurá-la em
uma área teste permite aos administradores fazerem testes nessa versão
sem colocar em risco o site no ar. O clone pode ser criado em uma
máquina local ou servidor que suporte os mesmos requisitos técnicos do
site original.

É fácil confundir o site teste com o site no ar. Tenha uma cor diferente
para cada uma das versões para que os administradores possam diferenciar
mais facilmente.

## Back Up a Joomla Website Using Akeeba (Common method)

This is the preferred method using the Akeeba Backup Extension.

- Akeeba Backup produces a *.jpa* file.
- The compressed *.jpa* file contains all the Website's files and the
  content of the database.
- The *.jpa* file also includes an installer.
- Akeeba's *kickstart.php* unpacks the *.jpa* file.
- You then run the installer and install your site like a Joomla
  install.
- The installer changes the configuration for restoring to a different
  location and prompts for the new database details.

You can download the Akeeba Backup extension from the <a
href="https://extensions.joomla.org/extensions/extension/access-a-security/site-security/akeeba-backup/"
class="external text" target="_blank" rel="noreferrer noopener">Joomla
extension directory</a>. There is a link to full instructions there as
well.

## Introdução

A cópia de um site em Joomla é feita em duas partes. São:

1.  A informação do banco de dados, normalmente encontrada no seu banco
    de dados MySQL.
1.  Os arquivos e pastar do seu site como estão no servidor.

Se não fizer a cópia dos arquivos e do banco de dados, ela estará
incompleta.

## Cópia do Banco de Dados Parte 1 de 2

O primeiro passo antes de começar a cópia de segurança de seu site em
Joomla é colocá-lo em manutenção, copiar os arquivos e depois irá-lo de
manutenção. No administrador do seu site, em Configurações Globais, na
aba Site, campo Site em Manutenção marque Sim.

Isso modificará o arquivo configuration.php na raiz do seu site em
Joomla.

An administrator will need to use your hosting control panel to view
that file or use FTP to download and view the file. Inside the
*configuration.php* file you can find the name of your database that
will need backing up.

Look for the line with code resembling `var $db = 'x1234';` or
`public $db = 'x1234';` Where *x1234* is the name of your database.

Using the logon information for your server or hosting company open the
phpMyAdmin tool. Open the database and look for the table named *users*
and then click the icon to *view* the data in that table.

You should see the names of staff who have accounts on your Joomla site.
This view provides you the confidence that you are about to backup the
correct database.

Click the *export* tab, then *Go*.

Your browser will download your database into an SQL file.

Find where you browser put that file, then move the file to a much more
secure drive or location.

Server SQL databases can be backed up without phpMyAdmin and instead
using the SQL command line. If you know how to do that, you're most
likely not in need of this documentation.

It is recommended that you back up the database at least twice per week
or even everyday (and more) if you have an active site.

### File System Backup

Continue with your site offline, see above. Your Joomla folder and files
can be backed up by downloading them with an FTP utility or using the
file manager of your web hosting company. Both of these file options
work, neither is better.

FTP tools move thousands of Joomla files and use more time. The FTP
process can be slow and interrupted. Most hosting companies provide a
control panel for taking thousands of files in one folder and then
creating a zip file very quickly.

This means your site is offline for a shorter amount of time and you
have only one zip file. Go to your hosting control panel and look for
their file manager icon.

If you use your hosting file manager, practice using that interface to
select your server folder and creating a zip file. Download the zip file
locally and then expand it locally to to see what files are inside that
zip file. This option also let's you expand the same zip file for
restoration to a staging site.

Backing up the Joomla files with FTP is no different than backing up a
static HTML website. Download all the files and folders that exist in
the main Joomla directory. The downloaded location is a folder on your
local computer. Be sure that the file and directory structure remains
the same as it is in the live site. When you restore the files, you will
use the FTP utility to upload the files to a new server.

**As soon as you've downloaded your files, via zip or FTP, change your
site to be online.**

## More Backup Documentation

Most administrators of a Joomla website have access to their MySQL data
using the GUI interface called phpMyAdmin, see <a
href="https://docs.phpmyadmin.net/en/latest/faq.html#how-can-i-backup-my-database-or-table"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">How can I backup my database or
table?</a> for more information.

There are several automated backup extensions for Joomla! located in the
<a href="https://extensions.joomla.org/" class="external text"
target="_blank" rel="noreferrer noopener">Joomla! Extensions
Directory</a>. Here is a link for <a
href="https://extensions.joomla.org/extension/?searchall=backup&amp;controller=filter"
class="external text" target="_blank" rel="noreferrer noopener">Joomla!
Backup Extensions</a>.

When servers are hosted in the same building as the staff, the web
administrators should make extra care to store the backup copies of the
database and files in a different building. Fire, theft, water or other
damage often wipes out the live website **and** backups. On a regular
basis the web administrators should burn both the database and files to
a CD or save to an external hard drive off site.

## Special Notes

### Two Factor Authentication (2FA)

If you use two factor authentication (available since Aug 2014) and you
are locked out of your site, you can rename the folder
*plugins/twofactorauth* to *twofactorauth.BAK* and log in to your site's
back-end. Then disable all plugins under the *twofactorauth* group.
Finally, rename the *plugins/twofactorauth.BAK* folder of your site to
*twofactorauth*.

- See also the  Two Factor
  Authentication
  tutorial.
