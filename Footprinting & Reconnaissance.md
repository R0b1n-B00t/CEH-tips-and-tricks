## Footprinting & Reconnaissance


- [x] In this guide *Linux* commands are anticipated by **#** while *Windows* ones are preceded by **>**. If no one character is present, it means that the command works in both OSes.


- [ ] Display the actual network configuration

  `> ipconfig`
  
  `# ifconfig` or `# ip a`
  
- [ ] Check Global/External IP address

  `curl ifconfig.me`

- [ ] Resolving host names using the Ping command

```
  ping www.starwars.com
  
  PING 23.12.146.154 (23.12.146.154) 56(84) bytes of data.
  64 bytes from 23.12.146.154: icmp_seq=1 ttl=47 time=0.696 ms
  64 bytes from 23.12.146.154: icmp_seq=2 ttl=47 time=0.748 ms
  64 bytes from 23.12.146.154: icmp_seq=3 ttl=47 time=0.756 ms
  
  --- 23.12.146.154 ping statistics ---
  3 packets transmitted, 3 received, 0% packet loss, time 2056ms
  rtt min/avg/max/mdev = 0.696/0.733/0.756/0.034 ms
```

- [ ] Find the Path’s MTU with Ping

```
  > ping 1.1.1.1 -f -l 1500
  
  Pinging 1.1.1.1 with 1500 bytes of data:
  Packet needs to be fragmented but DF set.
  Packet needs to be fragmented but DF set.
```
```
  > ping 1.1.1.1 -f -l 1400
  
  Pinging 1.1.1.1 with 1400 bytes of data:
  Reply from 1.1.1.1: bytes=1400 time=39ms TTL=54
  Reply from 1.1.1.1: bytes=1400 time=46ms TTL=54
```
  That means the path MTU between our source and destination is somewhere between 1400 and 1500 bytes.
  
  The same thing can be done in Linux, only the command syntax changes:

```
  # ping 1.1.1.1 -s 1500
  
  PING 1.1.1.1 (1.1.1.1): 1500 data bytes
  ping: sendto: Message too long
  ping: sendto: Message too long
```
  
```
  # ping 1.1.1.1 -s 1400
  
  PING 1.1.1.1 (1.1.1.1): 1400 data bytes
  1400 bytes from 1.1.1.1: icmp_seq=0 ttl=128 time=0.714 ms
  1400 bytes from 1.1.1.1: icmp_seq=0 ttl=128 time=0.619 ms
```

- [ ] Loading information into Metasploit

  `# service postgresql start`
  
  `# msfconsole`
    
  `# msf> msfdb init`

  `# msf> db_status`
  
  `# msf> run nmap -Pn -sS -A -oX SubnetScan 10.10.10.1/24`
  
  `# msf> db_import SubnetScan`
  
  `# msf> hosts`
  
  `# msf> services`


- [ ] Additional useful tools to know

* [Path Analyzer Pro](https://www.pathanalyzer.com/)
* [HTTrack](https://www.httrack.com/)

  
