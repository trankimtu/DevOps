# DevOps - IIS

IIS Manager
Add Website
  Site name
  Physical path:
  http/https - IP Address - Port
  Run Hello World! project
Add PHP mappings
    https://windows.php.net/download/
    Download zip file - Extract and Copy to C:\Program Files
    
    IIS - Handler Mappings -> Add Module Mapping
    Request path: *.php
    Module: FastCgiModule
    Executable: C:\Program Files\PHP\php-cgi.exe

    IIS - Default Document -> Add
    Name: index.php
    Move to top
Add Static IP Address
    Control Panel\All Control Panel Items\Network and Sharing Center -> Local Area Connection -> Property -> Internet Protocol Version 4 (TCP/IPV4) -> Advanced -> Add
    IP
    Subnet mask
    Check port open or closed - if it's closed, contact firewall open it
    https://portchecker.co/
Inbound Rules - Port
    New Rule -> Port -> TCP, Specific local ports: 443 -> Allow the connection -> check all: Domain, private, public -> Name and Description
