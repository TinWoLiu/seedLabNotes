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

<span style="font-size: 10em;">**Task 1.1A:**</span>
Use command 'ifconfig' to check the the iface of the machine.
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
