## Reminder Commands

sudo <command>: executes a command with administrator rights
apt update: updates the list of available packages to be installed
apt install package: installs the given package in the system
a2enmod <module>: enables an Apache2 module
a2ensite <module>: enables an Apache2 website
nano <file>: opens a text editor to edit the file
service <service name> restart: restarts the indicated service
ls <directory>: lists the files in a directory
cp <old> <new>: creates a copy of the old file with the new name
cat <file>: outputs the whole contents of a file
grep <pattern> <file>: filters the text of a file according to the pattern
tail <file>: shows the last lines of a file

## BackupPc commands
Install the backuppc package 
```
# sudo apt update 
# sudo apt install backuppc
```
Enable the SSL module
```
# sudo a2enmod ssl
```
Enable the default SSL site
```
# sudo a2ensite default-ssl.conf
```
Enable SSL in BackupPc - Edit config file wit nano and uncomment the SSLRequireSSL option
```
# sudo nano /etc/backuppc/apache.conf
```
Set the admin password of backuppc user
```
# sudo htpasswd /etc/backuppc/htpasswd backuppc
```
Restart apache2
```
# sudo service apache2 restart
```
Access the backuppc admin interface by appending /backuppc/ to the server URL

Edit the sudoers file
```
# sudo visudo
```
Add the following line to the sudoers file to allow backuppc to execute /bin/tar directly
```
# backuppc ALL=(ALL:ALL) NOPASSWD:/bin/tar
```
Switch to backuppc user
```
# sudo su - backuppc
```
Create an SSH key for the backuppc user
```
# ssh-keygen
```
Look at directory where keys were generated
```
# sudo ls -l /var/lib/backuppc/.ssh/
```
Copy the public key file to /tmp to access it without admin rights
```
# sudo cp /var/lib/backuppc/.ssh/id_rsa.pub /tmp/
```
Redirect public key to append it to the authorized_keys file
```
# cat id_rsa.pub | sudo tee -a /root/.ssh/authorized_keys
```
