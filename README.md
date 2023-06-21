# cyberwarder-almanac

--

This aims to be a list dedicated to helping within CTFs. 

--

Contents
    - Recon
        - Nmap

--


## Recon

--
### Nmap

#### Helpful flags

1. -F   [Scans top 100 ports]
2. -sU  [Performs a UDP scan] 

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

