Install Apache2 web server
```
# sudo apt update
# sudo apt install apache2
```
List of sites that are available for use on the Apache web server
```
# ls -l /etc/apache2/sites-available 
```
Move the website to standard location where websites are usually stored
```
# sudo mv /opt/devel/ourcompany /var/www/ourcompany
```
Enable and disable site symlinks in Apache2 
```
# sudo a2ensite 001-ourcompany.conf
# sudo a2dissite 000-default.conf
```
Reload the Apache2 Web server 
```
# sudo service apache2 reload
```
