# DevOps - IIS

## Instalation
[Download and install Microsoft Virtual C++](https://learn.microsoft.com/en-us/cpp/windows/)<br>
Download PHP non-thread version, extract to C:/PHP<br>
Edit the system environment variables > Under system variables > Path > Edit > New > Browse to c:\PHP <br>
Install CGI > Add roles and Features > Server Roles > Web Server (IIS) > Web Server > Application Development > Check CGI
## IIS Manager
### Add Website
  <ul>
    <li> Site name </li>
    <li> Physical path: </li>
    <li> http/https - IP Address - Port </li>
  </ul>
  
  
 
### Run Hello World! project
  <ul>
    <li> index.html </li>
    <li> index.php </li>
  </ul>
  
### Add PHP mappings

    Download zip file Thread Safe - Extract and Copy to C:\Program Files
    https://windows.php.net/download/
    
    <br>
    
    IIS - Handler Mappings -> Add Module Mapping
  <ul>
    <li> Request path: *.php </li>
    <li> Module: FastCgiModule </li>
    <li> Executable: C:\Program Files\PHP\php-cgi.exe </li>
  </ul>


    IIS - Default Document -> Add
    <ul>
      <li> Name: index.php </li>
      <li> Move to top </li>
    </ul>
    
    
## Add Static IP Address

    Control Panel\All Control Panel Items\Network and Sharing Center -> Local Area Connection -> Property -> Internet Protocol Version 4 (TCP/IPV4) -> Advanced -> Add
    <ul>
      <li> IP </li>
      <li> Subnet mask </li>
    </ul>  
    
    
    Check port open or closed - if it's closed, contact firewall open it <br>
    https://portchecker.co/
## Inbound and Outbound Rules - Port
    New Rule -> Port -> TCP, Specific local ports: 443 -> Allow the connection -> check all: Domain, private, public -> Name and Description


https://www.namecheap.com/support/knowledgebase/article.aspx/9640/69/how-to-export-certificates-between-windows-servers/
