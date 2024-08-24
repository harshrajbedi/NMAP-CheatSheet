## To scan multiple hosts at once
nmap 192.168.1.10 wahesec.com asset.wahesec.com

## To scan range of IP
nmap 192.168.1.10-20

## To scan using a list of hosts
nmap -iL list_of_hosts.txt

## To see details of the targets without scanning them
nmap -sL 192.168.1.10

## To disable the use of DNS resoultion in above command
nmap -sL 192.168.1.10 -n

## To perform ARP ping scan along with port scan
nmap -sn 192.168.1.10

## To perform ARP without port scan
nmap -PR -sn 192.168.1.10

## To perform ICMP echo scan without port scan
nmap -PE -sn 192.168.1.10

## To perform ICMP timestamp or address mask request
nmap -PP -sn 192.168.1.10

## To perform ICMP address mask queries
nmap -PM -sn 192.168.1.10

## To perform TCP SYN ping without port scan
nmap -PS -sn 192.168.1.10

## To perform TCP SYN ping without port scan on specific ports
nmap -PS80,443 -sn 192.168.1.10

## To perform TCP ACK ping without port scan
nmap -PA -sn 192.168.1.10

## To perform TCP ACK ping without port scan on specific ports
nmap -PA80,443 -sn 192.168.1.10

## To perform UDP ping without port scan
nmap -PU -sn 192.168.1.10

## To prevent sending DNS queries (Add -r Flag)
-r

## To query DNS server for offline hosts (Add -R Flag) 
-R

## To add specific DNS server
--dns-servers DNS_SERVER

## TCP connect scan (Completing 3-way handshake)
nmap -sT 192.168.1.10

## TCP connect scan using fast mode by scanning ports upto 1000
nmap -sT -F 192.168.1.10

## TCP connect scan by adding consecutive order instead of random order
nmap -sT -F -r 192.168.1.10

## TCP SYN scan (Incomplete 3-way handshake) (Stealth Scan)
nmap -sS 192.168.1.10

## UDP port scan
nmap -sU 192.168.1.10

## Some arguments to increase the performance or narrow down the results

-p22,80....
-p10-80
-p-
-F
--top-ports 10

## Controll the scanning time (T0=[slowest] & T5 [fastest])
-T(0-5) (T0 T1 T2 T3 T4 T5)

## Controll the packet rate (per second)
--min-rate (num)
--max-rate (num)

## Control Probing Parallelization
--min-parallelism <numprobes>
--max-parallelism <numprobes>
Example -> --min-parallelism=512

## Null scan (no flag set)
sudo nmap -sN 192.168.1.10

## FIN scan (FIN flag set)
sudo nmap -sF 192.168.1.10

## Xmas scan (FIN, PSH, and URG flags set)
sudo nmap -sX 192.168.1.10

## TCP maimon scan (FIN and ACK flags set)
sudo nmap -sM 192.168.1.10

## TCP ACK scan (ACK flag set)
sudo nmap -sA 192.168.1.10

## TCP window scan (Similar to ACK scan)
sudo nmap -sW 192.168.1.10

## Custom scan (set flags as per requirements)
nmap --scanflags CUSTOM_FLAGS 192.168.1.10
Example 1 -> nmap --scanflags RSTSYNFIN 192.168.1.10
Example 2 -> nmap --scanflags URGACKPSHRSTSYNFIN 192.168.1.10 (SETS ALL FLAGS)

## To spoof IP in the NMAP scan
nmap -S SPOOFED_IP 192.168.1.10

## To specify the network interface
nmap -e NET_INTERFACE -S SPOOFED_IP 192.168.1.10

## To explicitly disable the Ping scan
nmap -e NET_INTERFACE -Pn -S SPOOFED_IP 192.168.1.10

## To spoof the MAC address in the NMAP scan
--spoof-mac SPOOFED_MAC_ADDRESS

## NMAP Decoy Scan
nmap -D 10.10.0.1,10.10.0.2,ATTACKER_IP 192.168.1.10

## To fragement packets
nmap -sS -p80 -f 192.168.1.10 OR nmap -sS -p80 -ff 192.168.1.10

-f = IP data will be divided into 8 bytes
-ff = IP data will be divided into 16 bytes and so on
-mtu = To change the MTU value
--data-length NUM = To increase the size of the packet in bytes

## To perform Idle/Zombie scan
nmap -sI ZOMBIE_IP 192.168.1.10

## Adding more output to the NMAP scan
--reason = To get more details regarding the NMAP reasoning and conlusion in a reason column
-vv = For more verbosity
-d = For debugging
-dd = For intense debugging

## To collect and determine service version along with version intensity
-sV
--version-intensity (0[lightest] - 9[complete])
--version-light = Equals to 2
--version-all = Equals to 9

## For operating system detection
nmap -sS -O 192.168.1.10

## To find routes between the target machine
sudo nmap -sS --traceroute 192.168.1.10

## NMAP scripting engine (Default Script)
nmap -sS -sC 192.168.1.10
Default Location = /usr/share/nmap/scripts
-sC OR --script=default (To use the default script)

## To use NMAP non-default scripts
nmap -sS --script "SCRIPT_NAME" 192.168.1.10

## Save NMAP output as .nmap
nmap -sS -oN FILE_NAME 192.168.1.10

## Save NMAP output as grepable format .gnmap
nmap -sS -oG FILE_NAME 192.168.1.10

## Save NMAP output as XML file
nmap -sS -oX FILE_NAME 192.168.1.10

## To save NMAP output in all three formats (.nmap, .gnmap and .xml)
nmap -sS -oA FILE_NAME 192.168.1.10

## To save the NMAP in script kiddie format .kiddie
nmap -sS -oS FILE_NAME 192.168.1.10
