**MÉRÉSI JEGYZŐKÖNYV**

**Távkozlelési technikus vizsgafeladat**  
**Bit hibaarány mérése optikai összeköttetéssel**

---

**1. Mérés helye és időpontja:**  
- Helyszín: Telekom Labor
- Dátum: 2025.02.11.


**2. A vizsgázó neve:**  
- Név: Sándor Zsombor

**3. Feladat leírása:**

Áramkör tesztelése egy szándékosan küldött bit hibával.

**4. Sükséges eszközök:**  

- 2 db Catalyst 3560 switch
- EXFO FTB-200 Packet Analyzer, Ethernet and Fiber Tester
- JDSU OLA55 programozható csillapító
- UTP valamint Optikai (LC/PC és FC/PC) kábel
- HP céges laptop
- 2 db RMC Tel SFP-GE-LX CC sfp 1310nm
- ETS-1000L Ethernet Loopback

**5. Mérések és beállítások:**

Miután összekötöttük a hálózatot, következő lépésként bekötöttük az állítható csillapítót. A csillapító előtti értékeket itt lehet látni:

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 52.2          | 3.17       | -5.6          | -9.2          |

Melyet 1310nm-re és 10dB-re állítva használtunk. Így nálam már csak -16dB volt mérhető. Az adásom pedig -5,6 körül volt.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 52.7          | 3.17       | -5.6          | -16.6         |

17,45dB-es csillapításnál már -24 dB volt a fogadásom.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 52.7          | 3.17       | -5.6          | -24.1         |

Ekkor már riasztott is nálam hiszen alapértékként már 23dB-nél Alarm 22dB-nél pedig Warning üzenetet küld. Ennél a pontál már hibázott is, a műszer jól mutatta. 

#### *Mar  1 00:41:15.301: %SFF8472-5-THRESHOLD_VIOLATION: Gi0/3: Rx power low alarm; Operating value: -24.1 dBm, Threshold value: -23.0 dBm.

24,6dB-es csillapításnál szét is dobta a hálózatot, ekkor már -31.5dB-t mért.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 53.2          | 3.17       | -5.7          | -31.5         |

23,5dB-es csillapításnál állt helyre újra a kapcsolat, ekkor -30dB-es jelet kaptam.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 53.2          | 3.17       | -5.7          | -30.4         |


***5.1. Összekötés:***



***5.1. valami:***
***5.1. valami:***
***5.1. valami:***
***5.1. valami:***
***5.1. valami:***

***5.1. valami:***



**6. Összegzés:**



***6.1. Reflexió:***
