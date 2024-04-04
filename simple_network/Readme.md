# Simple Network for Hackers Poulette Startup
Project type: Solo <br>

## Project Context
Hackers Poulette a young startup that has just been created calls on your services to begin the installation of their infrastructure.

For now, there are only three people working on it, and all on the same set. But Robert Tappan Morris, the CEO, insists on the fact that Hackers Poulette is bound to grow, that the ambitions of the startup are great. So he wants an installation that is easily scalable. All three hosts must also be connected to the internet


## Goal
To establish a simple scalable network for the startup
- configure interconnectivity between hosts
- connect hosts to the internet

## Software Used
The network infrastructure was designed using Cisco Packet Tracer

## Resources Used
For the local network
- 1 router
- 1 switch
- 3 PCs
- 1 printer
- 1 DNS server

For internet access simulation
- 1 router
- 1 web server

## Configuration steps
### 1. Setup local network
**Physical connection**: The 3 PCs, DNS server, and a printer are connected via the FastEthernet ports to the switch using ethernet cables to establish a single LAN. The switch is then connected to a router (router1) which serves as the gateway to the LAN. <br>

**Logical connection**: Configure each device and interface/port with assigned IP addresses as shown in the addressing table below. For the PCs, populate the DNS field with the DNS IP address. Activate the interfaces and ensure they are up and running. <br>

**DNS configuration**: The local DNS server is provisioned by turning on the DNS service in the server settings. An A-record entry is made with the domain name and ip address of the remote web server as follows: <br>
    Domain name: www.cisco.srv <br>
    IP address: 192.168.2.254

*Note: The IP address was used only for simulation purposes. It does not map to the stated domain name in real world.*

**Addressing table :**

| Devices | LAN | IP | Mask |
|---------|-----|----|------|
| PC-Robert | Eth | 192.168.1.10 | 255.255.255.0 | 
| PC-Camille | Eth | 192.168.1.11 | 255.255.255.0 |
| PC-Renaud | Eth | 192.168.1.12 | 255.255.255.0 |
| Printer | Eth | 192.168.1.13 | 255.255.255.0 |


### 2. Simulate Internet access
**Physical connection**: A web server is deployed in a simulated remote network which is connected to a gateway router (router2) via ethernet cable. Router1 is then linked to router2 through the serial connection ports. This procedure allows the LAN to access the remote web server.  

**Logical connection**: IP addresses are assigned as shown in the addressing table. Activate the interfaces and ensure they are up and running.

**Web Server Configuration**: The web server is activated by enabling HTTP in its service settings on cisco packet tracer. In real world, this would correspond to listening on port 80.

### 3. Interconnectivity between hosts
The end devices can now communicate with one another in the network. This can be checked by sending a ping request from one host to the other via the command line interface. 
``` 
$ ping _<ip address>_
```

## Connection to the Internet
The hosts can now access the webserver on remote network. To test this, use a browser on a host PC to reach ```www.cisco.srv```, the default Cisco Packet Tracer webpage will be displayed.

## Possible Errors
An attempt to reach the internet on a browser may display "Host Name Unresolved." This is a DNS configuration problem. Check to ensure all DNS settings have been correctly implemented as described above.