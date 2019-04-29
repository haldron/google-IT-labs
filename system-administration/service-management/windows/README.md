To use the GUI for managing services -
Control Panel -> System and Security -> Administrative Tools -> Services

## With PowerShell
List the available services
```
# Get-Service
```
Get information about status of a specific service
```
# Get-Service wuauserv
```
Get more information about a specific service
```
# Get-Service wuauserv | Format-List *
```
Stop a service
```
# Stop-Service wuauserv
```
Start a service
```
# Stop-Service wuauserv
```
Enable a disabled service
```
# Set-Service ScardSvr -StartupType Manual
```
Install new web service features not enabled by default on Windows Server
```
# Install-WindowsFeature Web-WebServer,Web-Mgmt-Tools -IncludeAllSubFeature
```
Check the service used for publishing web pages
```
# Get-Service w3svc
```
To configure the web server , open the Internet Information Services (IIS) Manager
