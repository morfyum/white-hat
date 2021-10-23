# LINKS
```
# nmap script docs:
  - https://nmap.org/nsedoc/
# vulnhub.comm
  - https://vulnhub.com
```

```
# SWITCHES:	  TARGET		  DESCRIPTION
  -O		      only 1	  	-> OS Detection
  -A		      only 1	  	-> Enable OS detection, version detection, script scanning, and traceroute
  -p 		      more		    -> Scan specific ports on 1 or more host: `nmap -sT -p 80,443 192.168.99.195/24`
  -p-	        1 or more	  -> Scan all port on targert
  -s
  -S      	  1 or more	  -> Spoof source address (Firewall/ids Evasion and Spoofing) 
  -T	        1 or more	  -> Set timing template (highter is faster): T0,T1,...T5
  -v          1 or more	  -> Increase verbosity levele ( use -vv or more for greater effect)
  -P
  -n          ?		      -> No DNS resolutin (Tells Nmap to never do reverse DNS)
```

## Related tools
> Check your ip / network informations on Linux
```
ip a 
```



# [ SCAN ] : SUBNET / IP-RANGE 

### LIST CONNECTED DEVICES ON NETWORK WITH NAMES:

> TODO: Subnet /24 or IP-range 192.168.99.1-165
```
sudo nmap -sn 192.168.99.165/24
```

> Scan open specified ports on Network: 80, 443
```
sudo nmap -sT -p 80,443 192.168.99.165/24
```

> Scan open ports on Network as Stealthly
```
sudo nmap -sS -p 80,443 192.168.99.165/24
``` 

# [ TARGET ] : Gateway [ SCAN ] : Open ports

> Find the Gateway:
```
traceroute google.com
```

> Chekc the GATEWAY IP:
```
sudo nmap 192.168.99.253
```

> TODO
```
sudo nmap -sS -v -v -Pn 192.168.99.253
```

### [ TARGET ] : Windows
> Scan port over closed port:
> Bypassing Windows IPSec filter using source port
```
sudo nmap -sS -v -v -Pn -g 88 192.168.99.253
```


# [ SCAN ] : Single IP Target

> `-A` is equal with OS detection, version detection, script scanning, and traceroute
```
sudo nmap -A 192.168.99.119
```

> Vulnerability Check
```
sudo nmap --script vuln 192.168.99.119
```

### [ TARGET ] : Apple devices
> apple vnc port check
```
sudo nmap -p 5900 -sV -Pn -v 192.168.99.119
```

> AFP Server Info (548 : TCP) 
> This is give back your target MAC address
```
sudo nmap -p 548 -Pn -v --script "afp-serverinfo" 192.168.99.119
```


> Scan all Open port on host:
```
sudo nmap -p- 192.168.99.165
```
