downloading the docker zip file into the shared folder of the VM. Unzip the docker file and run the docker-compose.yml.
commands:
"docker-compose up -d" or "dcup" (use to initiate the docker).
"dockps" (list all the docker connections).
![picture of dockps and ping](screenshots/lab1/ping.png)

Open wireshark and use the filter on the top bar for "icmp" to see the ping traffic between attacker(hostA) to hostB.
![picture of wireshark](screenshots/lab1/wireshark.png)
![picture of icmp ping](screenshots/lab1/wiresharkPing.png)

After finished using docker, use "dcdown" to shutdown existing connections.
![picture of icmp ping](screenshots/lab1/dcdown.png)

## **Task 1.1A:**
Use command 'ifconfig' to check the the iface of the machine, 'br-7652d9fd4808' in this case (note that every time when you initiate docker, the iface can be different.)
![picture of ifconfig](screenshots/lab1/ifconfig.png)

Create a python script to sniff icmp traffic, in this case the file is named "sniffer1.py", and execute the python script with "sudo python3 'filename', in this case 'filename' is 'sniffer1.py'.
![picture of sniffer1.py](screenshots/lab1/sniffer1.png)

In another terminal, use 'dockps' to check the container ips, and use 'docksh' to execute a container.
![picture of docksh](screenshots/lab1/docksh.png)

Use the 'ping' command to ping a host which generate icmp traffic, go to the terminal which is running 'sniffer.py', observe the capture icmp packets
![picture of packets](screenshots/lab1/icmpPacket.png)

Change the script instead of ".show()" to ".summary", but ".summary()" does not automatically print in the terminal, so the new line of code would be "print(pkt.summary())".
![picture of sniffer1 with .summary()](screenshots/lab1/sniffer1summary.png)
![picture of packets as summary](screenshots/lab1/icmpPacketSummary.png)

## **Task1.1B**
Create a new sniffer script similar to 'sniffer1.py' to sniff tcp traffic, change the filter from 'icmp' tp 'tcp'.
![picture of sniffer2.py](screenshots/lab1/sniffer2.png)

Enter hostB container, and telnet into hostA to create tcp traffic. Observe the tcp packets captured by the new sniffer.
![picture of telnet](screenshots/lab1/telnet.png)
![picture of packets of tcp](screenshots/lab1/tcpPacket.png)

Create a new sniffer script but for specific subnet, change the filter to 'net 128.230.0.0/16'.
![picture of sniffer3.py](screenshots/lab1/sniffer3.png)

Ping from any of the container, and use 'ping 128.230.0.11' to ping the entire subnet('ping -c 4 128.230.0.11' to limit the pings to 4).
![picture of ping subnet](screenshots/lab1/pingSubnet.png)
![picture of packets of subnet pings](screenshots/lab1/subnetPacket.png)

As the ifconfig picture above, the subnet mask of the iface is '255.255.255.0', which means that the subnet is /24, 256 addresses total (254 usable, .0 and .255 are reserved for network and broadcast address).