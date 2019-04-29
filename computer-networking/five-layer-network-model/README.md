## The 5-Layer Network Model in Action

### PROMPT
In your own words, describe what happens at every step of our network model when a node on one network establishes a TCP connection with a node on another network. You can assume that the two networks are both connected to the same router.

### Assumptions -

1.      As given, we can assume two nodes are on different networks which have a common router between them. The node Computer A on Network A tries to establish a TCP connection with node Computer B on Network B.

2.      For the sake of explanation using an example let's say Computer A on Network A wants to get a webpage located on Computer B on Network A.

3.      IP of computer A is 10.1.1.100 on the network A at 10.1.1.0/24 and IP of computer B is 192.168.1.100 on the network B at 192.168.1.0/24. Router interface on network A is 10.1.1.1 and on network B is 192.168.1.1


### Steps involved -

1. Browser on Computer A needs to access the webpage at 192.168.1.100 on port 80. It creates a request to its local network stack in the operating system to establish a TCP connection to 192.168.1.100:80. The networking stack checks its subnet  on the current network, then using an AND operation, computes that the Computer B between the IP addresses and realizes that is on another network as the address is outside the LAN's IP range.

2. The computer A's OS networking stack looks at the ARP address table to determine the MAC address of 10.1.1.1, but as there is no entry in the ARP table, it sends an ARP discovery request broadcast to every node on the local network using the MAC address FF.FF.FF.FF.FF.FF. When the Router receives the request, it responds to only Computer A with its MAC address.

3. Computer A now knows the hardware address of it's gateway. So it prepares to send the original webpage request to the LAN gateway on the router at 10.1.1.1 to route it to a remote network. It creates an outbound TCP port on the ephemeral port 60000 and opens a socket connecting the web browser to this port. Now it prepares the packet headers which are added upon by each layer (TCP, IP and Data Link layers).

4. First the TCP header is added. It contains information like Source and Destination ports, Sequence number, Flags (SYN for connection request), Checksum for integrity of the packet and other headers, along with the original browser request as the data payload.

5. Then the IP layer adds the IP header to make the IP Datagram with information like Source and Destination IP, Time To Live(TTL), Checksum for integrity.

6. The Ethernet Datagram/Wireless Datagram is constructed to send the payload to the router MAC address. The Datagram has its own header with information like MAC addresses and calculated checksum for integrity. This ethernet frame data is then converted to binary and sent through the network interface.

7. The network interface card on Computer A sends the information as modulations of voltage of an electrical current across the cable or through wireless transmission to the router. 

8. The router receives the ethernet frame and recognizes the source and destination address. It checks the checksum values for Ethernet/Wireless, IP and TCP headers. It modifies the IP header for TTL Router hops and recalculates checksum. It modifies some other values in headers such as MAC address. It checks the destination IP and subnet mask and looks up its routing table for the best route it knows to send the data.

9. The router knows the other computer is on its other network gateway attached to Network B. Then it sends the datagram to Computer B using a similar process how Computer A sent the datagram to the router.  It checks the IP of the destination computer B and looks up its MAC address or finds it through an ARP discovery request. It re-encapsulates the TCP packet with new IP and Ethernet headers into a new datagram having destination address as Computer B. Then the datagram is forwarded to Computer B on Network B.

10. The Computer B receives the datagram and then checks and strips the headers for information. Finally, the data payload of the TCP packet is used to get the Application Layer HTTP request. If the Computer B was listening on a socket for a webpage hosted locally, it retrieves the webpage and sends it to the socket where it is formulated into a response datagram for Computer B.
