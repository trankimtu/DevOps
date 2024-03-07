# DevOps - IIS

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

    Download zip file - Extract and Copy to C:\Program Files
    https://windows.php.net/download/
    <br>
    IIS - Handler Mappings -> Add Module Mapping
  <ul>
    <li> Request path: *.php </li>
    <li> Module: FastCgiModule </li>
    <li> Executable: C:\Program Files\PHP\php-cgi.exe </li>
  </ul>
    
    <br>
    
    

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
## Inbound Rules - Port
    New Rule -> Port -> TCP, Specific local ports: 443 -> Allow the connection -> check all: Domain, private, public -> Name and Description


https://www.namecheap.com/support/knowledgebase/article.aspx/9640/69/how-to-export-certificates-between-windows-servers/
