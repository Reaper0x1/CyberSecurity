# CyberSecurity
 
## WIFI - Half-Handshake Attack 

```bash
ifconfig
``` 

-   Note **wlan0** (or your wireless network card name).

-   Enter monitor mode:
```bash
sudo airmon-ng start wlan0
```

```bash
sudo airodump-ng wlan0mon
```

-   After some seconds stop the monitor with **`CTRL-C`**.

-   Note the channel (**CH**) number of the target wireless network and note the MAC address (**BSSID**).

-   Set the wireless network card to the channel you noted before (replace N with the channel number) and open wireshark for network analysis.
```bash
sudo airodump-ng wlan0mon -c N & wireshark
```

-   On wireshark select the wireless network card wlan0mon.

-   Search a beacon frame:

    ![A hha 1](./Resources/WIFI/Half-Handshake%20Attack/beacon_frame_1.png)

-   Right click on Trasmitter address -> Apply as Filter -> Selected

-   Copy and pipe the same string as **`wlan.ta MAC address || wlan.da MAC address`** :

    ![A hha 2](./Resources/WIFI/Half-Handshake%20Attack/beacon_frame_2.png)

-   Press thi button on top bar:

    ![A hha 3](./Resources/WIFI/Half-Handshake%20Attack/beacon_frame_3.png)

-   Wait some time to capture people packets, then copy the strings writed before and finally type **`eapol`**(basically Hand-shake) in the same text area.

- Notice, those are hand-shakes:

    ![A hha 4](./Resources/WIFI/Half-Handshake%20Attack/beacon_frame_4.png)

- Now type **`eapol || wlan.ta MAC address || wlan.da MAC address`** in the toptext area, wait some seconds and press stop button at the top left.

-   Then click on the top left File -> Export Specified Packets... , save it with a name. Make sure you selected Displayed and in 'Export as:' pcap extension is selected.

-   Go back to your termina window and press **CTR-C** to close wireshark.

-   Run:
```bash
aircrack-ng -w /path/to/a/wordlist/file /path/to/previously/pcap/file
```

-   Now just wait for aircrack to check every password (converted to hash) inside the wordlist with the hash inside the packets.
