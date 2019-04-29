See the status of the network interface for server side
```
# ip address show eth_srv
```
Get the status of the dnsmasq service daemon
```
# sudo service dnsmasq status
```
Stop the dnsmasq service
```
# sudo service dnsmasq stop
```
Start the dnsmasq service manually with debug mode
```
# sudo dnsmasq -d -q
```
Check the local dns server on the machine with an example website
```
# dig example.com @localhost
```
Check config of dnsmasq already deployed
```
# cat /etc/dnsmasq.d/mycompany.conf
```
Main terms in the config -
1. interface - Name of interface used to listen to DHCP requests and serving replies
2. bind-interfaces - dnsmasq will operate on that interface only and ignore the others
3. domain - Domain name used on the network
4. dhcp-option - Allows us to give DHCP clients additional information such as router and dns server
5. dhcp-range - Range of IPs that are available to be used for dynamic IP assignment and the length of the lease

Run dnsmasq and tell it which configuration file we want to use 
```
# sudo dnsmasq -d - q -C /etc/dnsmasq.d/mycompany.conf
```
Use dhcp on client side linux using eth_cli interface in verbose mode with a debugging script
```
# sudo dhclient -i eth_cli -v -sf /root/debug_dhcp.sh
```
Verify syntax of modified configuration file that we want to use
```
# sudo dnsmasq --test -C /etc/dnsmasq.d/mycompany.conf
```
