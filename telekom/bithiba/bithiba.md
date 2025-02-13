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

Miután előkészítettünk minden szükséges eszközt, elkezdhettük összekötni őket. Elsősorban összekötöttük a két Switchet, optikai kábellel melyhez már az SFP-t is behelyztük mind ezt a GigabitEthernet 0/3-as portra. Valamint a GigabitEthernet 0/1-as portra az Én switchembe rákötöttük az Ethernet Loopback-et. A labor társam switchére pedig az EXFO Packet Analyzert. Valamint a switchekre nem kellett semmilyen komoly konfigurációt, csupán egy Vlan10-et kellett létrehoznunk, melyet engedélyeztünk a Gigabit Ethernet 0/1-en és 0/3-on. Ezeket a portokat access portnak konfiguráltuk.

Konfiguráció: 

```cisco
!
interface GigabitEthernet0/1
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
!
interface GigabitEthernet0/2
!
interface GigabitEthernet0/3
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
!
```

<details>
    <summary>Modellezés</summary>
    <img src="https://github.com/user-attachments/assets/eb851484-64db-45b1-9f60-f92858c86745" width="486" height="360">
</details>

<details>
    <summary>Összeépített hálózat</summary>
    <img src="https://github.com/user-attachments/assets/d7d9dfdc-c655-4546-aa76-673c61f4fa3a" width="640" height="360">
</details>

***5.2. RMC Tel SFP-GE-LX:***

Mivel ez volt az első SFP amit vizsgáltunk ezért, ezt néztük meg a legrészletesebben. A többi SFP-nél már csak a hibaarányt vizsgáltuk leginkább és csak pár jelszintet.

Miután összekötöttük a hálózatot, következő lépésként bekötöttük az állítható csillapítót. A csillapító előtti értékeket itt lehet látni:

| Port  | Temperature (°C) | Voltage (V) | Tx Power (dBm) | Rx Power (dBm) |
|-------|----------------|------------|---------------|---------------|
| Gi0/3 | 52.2          | 3.17       | -5.6          | -9.2          |

Melyet 1310nm-re és 10dB-re állítva használtunk. Így nálam már csak -16dB volt mérhető. Az adásom pedig -5,6 körül volt.

<details>
    <summary>Csillapítás</summary>
    <img src="https://github.com/user-attachments/assets/7e31ce6d-e2b6-4ee0-94fd-023d6d639207" width="360" height="640">
</details>

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

A mérések során különböző optikai modulokat vizsgáltunk, és meghatároztuk a hibahatárokat, valamint a kapcsolat megszakadásához vezető jelszinteket. A cél a hibaelhárítási folyamat megismerése, valamint az optikai linkek megbízhatóságának vizsgálata volt. 

- A mérések igazolták, hogy az optikai link stabilitása erősen függ a csillapítás mértékétől.
- Az optikai jelszintek következetes monitorozása elengedhetetlen a hibák időbeni felismeréséhez.
- Az SFP modulok eltérő képességekkel rendelkeznek a csillapítás tűrése terén, amit figyelembe kell venni a hálózati infrastruktúra tervezésekor.

A mérések során szerzett tapasztalatok segítségével pontosabban meghatározhatók az optimális konfigurációs beállítások, ezáltal biztosítható az optikai hálózat megfelelő működése és stabilitása.



***6.1. Reflexió:***

A mérés során végig motivált és lelkes voltam, hiszen lehetőségem nyílt egy komplex optikai rendszer vizsgálatára. A különböző eszközök konfigurálása és a hibaelemzés kihívást jelentett, ugyanakkor sikeresen teljesítettem a feladatot. Az eredmények pontosan igazolták az elméleti várakozásokat, ami különösen elégedettséggel töltött el.

A feladat során fejlődött a műszaki eszközök kezelésében szerzett tapasztalatom, és megerősítést nyert az optikai hálózatokkal kapcsolatos tudásom. A pozitív végkifejlet, az eredmények értelmezése és a sikeres hibadetektálás megerősítette bennem, hogy a szakmai fejlődésem jó irányba halad.
