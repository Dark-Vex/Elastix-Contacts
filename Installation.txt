1) Login into SSH on Elastix

mkdir /var/www/html/contacts/

2) Copy the files cisco.php and snom.php under /var/www/html/contacts/

3) Edit the apache configuration "/etc/httpd/conf.d/elastix-htaccess.conf" and append at the end of the file:

<Directory "/var/www/html/contacts">
    RewriteEngine Off
    Options -Indexes
</Directory>
 
Save the file and restart apache with "service httpd restart" and then test if the Phonebook works by calling the URL:
http://<pbx-ip>/contacts/cisco.php
http://<pbx-ip>/contacts/snom.php

- Configure the Cisco phones (tested on Cisco SPA502G and SPA504G)
Login into the Phone web interface (http://<phone-ip>/admin/advanced) and go under the "Phone" section and search for "XML Directory Service Name" and "XML Directory Service URL".
Under "XML Directory Service Name" put a name for the Phonebook
Under "XML Directory Service URL" put the link to the PBX "http://<pbx-ip>/contacts/cisco.php"
Then push "Submit all changes"

- Configure the Snom phones (tested on Snom320 and Snom360)
Login into the Phone web interface (http://<phone-ip>/fkeys.htm) and search for the Context "DIRECTORY".
Change the type from "Key Event" to "Action URL" and the put the URL "http://10.4.2.10/contacts/snom.php"
Save the configuration
