<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_IIS/IIS7 / Display title: Habilitando URLs amigáveis para mecanismos de pesquisas (SEF) no IIS7 -->

Se você tiver um servidor executando o IIS 7 e o PHP, poderá aproveitar
a própria reescrita de URL interna do IIS usando um arquivo web.config
semelhante ao listado abaixo.

Você pode criar o arquivo sozinho ou usar a interface gráfica do usuário
no gerenciador do IIS7. Você pode importar regras do .htaccess usando o
assistente da interface gráfica do usuário.

Esta funcionalidade depende da presença do **Módulo de reescrita de URL
do IIS**, que não vem com o Windows. É um download gratuito e um produto
da Microsoft.

### Interface gráfica do usuário

Se o módulo de reescrita de URL do IIS estiver instalado, o gerenciador
de seu site terá uma ferramenta para "reescrita de URL", visível na
exibição do gerenciador dos IIS dos módulos para IIS configuráveis do
seu site. A interface é amplamente auto-explicativa. Expressões
regulares, curingas ou correspondências exatas são todas suportadas.

Na configuração do Joomla, ative o mod_rewrite do SEF e do Apache, em
seguida, crie uma regra na reescrita de URL do IIS:

Pattern field: **^(\[^/\]+)/?\$**

Ignore case **ON**

Action type: **Rewrite**

Rewrite URL: **index.php/**

### web.config

Isso foi testado no Joomla 1.5 com IIS 7 no Windows Server 2008 sem
problemas até agora. Para obter mais informações sobre como converter
.htaccess para web.config, confira <a
href="http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/</a>


        
            
                
                    
                    
                        
                        
                            
                            
                            
                            
                            
                        
                        
                    
                    
                        
                        
                            
                        
                        
                    
                    
                        
                        
                            
                            
                            
                        
                        
                    
                
            
            
                
                    
                
            
        
