# cyberwarder-almanac

--

This aims to be a list dedicated to helping within CTFs.

--

## Contents

- Common Ports List

- Recon
  - Nmap

--

## Common Ports List

Fill in descriptions -
| Port | Protocol | Description|
|------|------|------------|
|20/21 | FTP| File Transfer Protocol|
|22| SSH | Secure Shell|
|22|SFTP| Secure File Transfer Protocol|
|23|Telnet| Telnet|
|25|SMTP|Simple Mail Transfer Protocol|
|53|DNS| Domain Name System|
|67/68|DHCP|Dynamic Host Configuration Protocol|
|69|TFTP|Trivail Transfer Protocol|
|80|HTTP|HyperText Transfer Protocol|
|110|POP3| Post Office Protocol V3|
|123|NTP|Network Time Protocol|
|143|IMAP|Internet Message Access Protocol|
|161/162|SNMP|Simple Network Management Protocol|
|389|LDAP|Lightweight Directory Access Protocol|
|443|HTTPS|HyperText Transfer Protocol Secure|
|445|SMB|Server Message Block|
|514|Syslog| Syslog|
|587|SMTP TLS| SMTP TLS|
|636|LDAPS|Lightweight Directory Access Protocol(over SSL)|
|1433|SQL|Structured Query Language Server|
|1521||SQLnet|SQLnet|
|3306|MySQL|MySQL|
|3389|RDP|Remote Desktop Protocol|

## Recon

--

### subdomain enum

first export target

```
export TARGET="DOMAIN"
```

Then curl output

```
curl -s "https://crt.sh/?q=${TARGET}&output=json" | jq -r '.[] | "\(.name_value)\n\(.common_name)"' | sort -u > "${TARGET}_crt.sh.txt"
```

### theHarvester sources.txt

```
baidu
bufferoverun
crtsh
hackertarget
otx
projecdiscovery
rapiddns
sublist3r
threatcrowd
trello
urlscan
vhost
virustotal
zoomeye
```

### whatweb

WhatWeb identifies websites contents, looking at things like CMS, libraries, webservers etc
changing the aggressiveness of the -a flag will make it more stealthly or agressive.

```
whatweb -a3 http://${TARGET} -v
```

### nslookup

basic nslookup
`nslookup $TARGET`

querying specific record
`nslookup -query=$RECORD $TARGET`

#### dig

basic dig
`dig $TARGET @<nameserver/IP>`

querying a specific record
`dig $RECORD $TARGET @<nameserver/IP>`

### Nmap

#### Helpful flags

1. -F [Scans top 100 ports]
2. -sU [Performs a UDP scan]

#### Commands List

##### Ping Network Sweep

Performs a ping sweep on the 10.0.0.0/24 subnet to discover which hosts are online

```
nmap -sP 10.0.0.0/24
```

##### Aggressive Full Port SYN Scan with Version Detection

Peforms a full port SYN(stealth) scan along with sevice version detection on all 65535 ports of the target using an aggressive speed

```
nmap -p- -sV -sS -T4 target
```

##### Agreesive Comphrehensive SYN Scan

Performs an aggressive stealth SYN scan with verbose output, OS detection, version detection, script scanning, and traceroute on the target.

```
nmap -v -sS -A -T4 target
```

##### Insane Speed Comprehensive SYN Scan

Similar to the aggressive comprehensive SYN scan, but uses the highest speed, which is less likely to be reliable but faster.

```
nmap -v -sS -A -T5 target
```

##### Insane Speed Stealth SYN Scan with OS and Verison Detection

Performs a stealth SYN scan with insane speed, including verbose output, service version detection, and OS detection on the target.

```
nmap -v -sV -O -sS -T5 target
```

##### Aggressive Full Port Stealth SYN Scan with OS and Version Detection

Performs a full port stealth SYN scan on all 65535 ports of the target, using aggressive speed, and includes OS detection and version detection.

```
nmap -v -p- -sV -O -sS -T4 target
```

##### Insane Speed Full Port Stealth SYN Scan with OS and Version Detection

Similar to the aggressive full port stealth SYN scan but uses the highest speed, which is faster but less likely to be reliable.

```
nmap -v -p- -sV -O -sS -T5 target
```

--
