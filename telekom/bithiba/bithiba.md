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
- 2 db RMC Tel SFP-GE-ZX CC sfp 1550nm
- 1 db RMC Tel SFP-GE-MBU-31D CC sfp TX1310nm, RX1490nm
- 1 db RMC Tel SFP-FE-MBD-49D CC sfp TX1490nm, RX1310nm
- ETS-1000L Ethernet Loopback

**5. Mérések és beállítások:**

***5.1. Összekötés és konfigurálás:***

Miután előkészítettünk minden szükséges eszközt, elkezdhettük összekötni őket. Elsősorban összekötöttük a két Switchet, optikai kábellel melyhez már az SFP-t is behelyztük mind ezt a GigabitEthernet 0/3-as portra. Valamint a GigabitEthernet 0/1-as portra az Én switchembe rákötöttük az Ethernet Loopback-et. A labor társam switchére pedig az EXFO Packet Analyzert.

***5.2. RMC Tel SFP-GE-LX:***

Mivel ez volt az első SFP amit vizsgáltunk ezért, ezt néztük meg a legrészletesebben. A többi SFP-nél már csak a hibaarányt vizsgáltuk leginkább és csak pár jelszintet.

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

Valamint 24,2dB-nél még nincs hiba, de 24,4dB-nél már elkezdődött a hibázás.

| Metric            | Value |
|------------------|-------|
| Input Errors     | 76    |
| CRC Errors       | 8     |
| Frame Errors     | 0     |
| Overrun Errors   | 0     |
| Ignored Errors   | 0     |
| Output Errors    | 0     |
| Collisions       | 0     |
| Interface Resets | 0     |

Ekkor meglepő módon, ugyan olyan bejövő szintet mértünk, mint amikor a hálózat szét esett.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 52.7          | 3.17       | -5.7          | -31.5         |



***5.3. RMC Tel SFP-GE-ZX:***

Ennél az SFP-nél már alapból behelyeztünk egy 10dB-es csillapítót is. Majd ennél az SPF-nél így mértünk hibaarányt és, hogy hol szakad meg a hálózat.

31,5dB-nél még nincs hiba, de 32,4dB-nél már elkezdődött a hibázás.

| Metric            | Value |
|------------------|-------|
| Input Errors     | 133   |
| CRC Errors       | 11    |
| Frame Errors     | 0     |
| Overrun Errors   | 0     |
| Ignored Errors   | 0     |
| Output Errors    | 0     |
| Collisions       | 0     |
| Interface Resets | 0     |

Ekkor az érkező szint -30,4dB volt.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 44.6          | 3.18       | 1.7           | -30.4         |

Majd mikor megszakadt a hálózat akkor -31dB volt.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 44.6          | 3.18       | 1.7           | -31.0         |

***5.4. RMC Tel SFP-GE-MBU-31D & RMC Tel SFP-FE-MBD-49D:***

Ennél az SFP-nél az az érdekesség, hogy egy szálat használ, nem pedig kettőt. Valamint ennél, 2 típust is használtunk, ahol különböző hullámon megy az adás és vétel.

Itt 22,7dB-nél még nincs hiba, de 23,4dB-nél már elkezdődött a hibázás.

| Metric            | Value |
|------------------|-------|
| Input Errors     | 669   |
| CRC Errors       | 41    |
| Frame Errors     | 0     |
| Overrun Errors   | 0     |
| Ignored Errors   | 0     |
| Output Errors    | 0     |
| Collisions       | 0     |
| Interface Resets | 0     |

Ekkor az érkező szint -31dB volt.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 55.8          | 3.17       | -6.3          | -31.0         |

Majd mikor megszakadt a hálózat, -31,5dB-t mértünk.

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 56.3          | 3.17       | -6.4          | -31.5         |


**6. Összegzés:**



***6.1. Reflexió:***
