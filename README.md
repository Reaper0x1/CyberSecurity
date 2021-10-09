# CyberSecurity
 
## WIFI - Half-Handshake Attack 
```
ifconfig
```

-   Note wlan0

-   Enter monitor mode:
```
sudo airmon-ng start wlan0
```

```
sudo airodump-ng wlan0mon
```

-   After some seconds stop the monitor with CTRL-CTRL

-   Note the channel (CH) number of the target wireless network and note the MAC address (BSSID)

-   Set the wireless network card to the channel you noted before (replace N with the channel number) and open wireshark for network analysis
```
sudo airodump-ng wlan0mon -c N & wireshark
```

-   On wireshark select the wireless network card wlan0mon

-   Search a beacon frame 

    ![A hha 1](./Resources/WIFI/Half-Handshake%20Attack/beacon_frame_1.png)

-   Right click on Trasmitter address -> Apply as Filter -> Selected

-   Copy and pipe the same string as `wlan.ta MAC address || wlan.da MAC address` :

    ![A hha 2](./Resources/WIFI/Half-Handshake%20Attack/beacon_frame_2.png)

-   Press thi button on top bar:

    ![A hha 3](./Resources/WIFI/Half-Handshake%20Attack/beacon_frame_3.png)