## Lab - Introducing tcpdump
Read packets constantly from eth0 network interface
```
# sudo tcpdump -i eth0
```
Read packets with verbose (-v) and prevent lookups and resolutions (-n)
```
# sudo tcpdump -i eth0 -vn
```
Read packets but filter based on host and port
```
# sudo tcpdump -i eth0 -vn host 8.8.8.8 and port 53
```
Use dig to query a DNS server (for seeing output in another terminal running packet capture)
Here 8.8.8.8 is the specified DNS server, and we want the A record for lookup of example.com
```
# dig @8.8.8.8 A example.com
```
Save captured packets a pcap file with filtering of port 80
```
# sudo tcpdump -i eth0 port 80 -w http.pcap
```
Fetch html in the terminal using terminal browser command (for seeing output in another terminal running packet capture)
```
# curl example.com
```
Open a pcap file to read it with tcpdump
```
# tcpdump -r http.pcap -nv
```

