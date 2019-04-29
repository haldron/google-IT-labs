## Reminder commands
```
sudo <command> - execute with admin rights
ls <directory> - list the files in the directory
mv <old_name> <new_name> - move or rename the file
tail <file> - see last lines of a file
cat <file> - print whole contents of the file
grep <pattern> <file> - filter the text of the file according to pattern
less <file> - Browse a file 
```

## Service Management
Listing system services which are running currently
```
# sudo systemctl --state=running
```
Check status of a service
```
# sudo service rsyslog status
```
Send text to the rsyslog service and write it to /var/log/syslog
```
# logger This is a test log entry
```
See the bottom of the syslog file for the latest log
```
# sudo tail -1 /var/log/syslog
```
Stop the syslog service
```
# sudo service rsyslog stop
```
Start the rsyslog service
```
# sudo service rsyslog start
```
Restart the rsyslog service (stop then start)
```
# sudo service rsyslog restart
```
List system services in a failed state
```
# sudo systemctl --state=failed
```
Manually change the date of the machine
```
# sudo date -s '2017-01-01 00:00:00'
```
Restart the ntp service which also fixes the date
```
# sudo service ntp restart
```
Reload a service (make it re-read its configuration without restarting it)
```
# sudo service cups reload
```
