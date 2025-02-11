**MÉRÉSI JEGYZŐKÖNYV**

**Távkozlelési technikus vizsgafeladat**  
**Mikro szakasz csillapitás modellezése, különböző vételi szinteknél labor körülmények között.**

---

**1. Mérés helye és időpontja:**  
- Helyszín: Telekom Labor
- Dátum: 2025.02.11.


**2. A vizsgázó neve:**  
- Név: Sándor Zsombor

**3. Feladat leírása:**

A feladat célja, hogy modellezük és megmérjük egy mikró szakasz rádiós paramétereit, különböző csillapításoknál. Majd mért eredményeink összehasonlítása, az ideális adatokkal. Mind ezt labor körülmények közötti kivitelezésben.

**4. Sükséges eszközök:**  

- NEC iPASOLINK VR4 beltéri egység
- ODU VR4 NEC iPASOLINK TRP-26G-1D kültéri egység (Felső oldalsáv)
- HP-P200 DC48V 4,2A (48V-os tápegység)
- Metex Digitális Multiméter
- Fix 20dB-el csillapító
- You Hewlett Packard állítható csillapít 0-70dB, 10dB-es léptékkel (Működési tartománya DC 26,5GHz)
- UTP és Koaxiális kábelek
- HP céges laptop

**5. Mérések és beállítások:**

***5.1. összekötés:***

Első sorban a beltéri egységeinket a tápegységgel összekötöttük és bekapcsoltuk azokat. Majd ezek után koax kábellel összekötöttük a mikrókat a beltéri eszközökkel. Mind ezekmellett duplex összeköttetést használtunk. A laptopot DHCP-be állítottuk, és Ethernet kábellel az eszköz LCT portjára csatlakoztunk. Majd egy webböngészővel beléptünk a konfigurációs felületre az alábbi IP segítségével: 
- http://172.17.254.253

Melyhez a belépéshez szükséges adatotak a gyártó adja nekünk meg. 
- Felhasználónév: Admin
- Jelszó: 12345678

<details>
    <summary>Valóságbani kinézete</summary>
    <img src="https://github.com/user-attachments/assets/761d868a-cb39-4578-9085-0caafe8cc76a" width="640" height="360">
</details>

***5.2. konfigurálás:***

Ahhoz, hogy legyen rádiós összekötettésünk, az alap rádiós paramétereket be kellett állítani.
- Channel Spacing: 28 MHz
- Referenc Modulation: QPSK
- TX Frekvencia: 25808 MHz
- TX Power Control: MTPC (Manual Transmission Power Control) 
Ha ez nincs beállítva akkor automatikusan növeli az adót és emiatt nem tudunk a csillapítással mérni.
- TX Power: 0 dBm (1 mW)
- AMR moduláció: QPSK, 16QAM, 32QAM, 64QAM, 128QAM, 256QAM
Ezzel állítottuk be, hogy QPSK és 256QAM között bármilyen modulációt felvehet, annak érdekében, hogy ne szakadjon meg.

Valamint meg kell említeni, hogy a gyakorlatban a mikrók vételi szintjét -35dB körülre szokták tenni.

<details>
    <summary>Konfig Felület kinézete</summary>
    <img src="https://github.com/user-attachments/assets/52572cab-e8b9-42c6-a755-cb0a3275f356" width="640" height="360">
</details>

***5.3. Csillapító tagok behelyezése és mérése:***

Az átalakító tag bekötése után, 3-3 dB csillapítást mértünk. Állítható csillapító mértéke: 0-70 dB, 10dB-es lépcsőkkel. Ezeknek a csillapítok segítségével modelleztük az időjárási viszonyokat.

---

| Csillapítás (dB) | 20   | 30   | 40   | 50   | 60   | 70   |
|----------------|------|------|------|------|------|------|
| Mért bejövőszint (dBm) | -35,8 | -45,7 | -54,2 | -64,7 | -73,8 | -84,1 |
| Mért feszültség (V) | 3,52  | 2,73  | 2,04  | 1,3   | 0,53  | 0,06  |
| Leolvasott moduláció TX | 256QAM | 256QAM | 256QAM | 256QAM | 128QAM | QPSK |
| Leolvasott moduláció RX | 256QAM | 256QAM | 256QAM | 256QAM | 64QAM  | QPSK |

---

Következő megállapításra jutottunk:
- Valamint 60dB-ig a modulációt egységesen megtartja, azonban felette elkezdi levenni őket.
- A jelünk 70dB-ig elfogadható azonban felette már szétesik a jelünk.
- Összeköttetés nélkül (szakadás esetén) -90dB mértünk.

<details>
    <summary>Feszültség mérérs</summary>
    <img src="https://github.com/user-attachments/assets/18087bdf-83f8-4211-a989-78578a59bde2" width="640" height="360">
</details>


Az adatok kigyűjtése után, már lehetőségünk lett, hogy összehasonlítsuk a mért és ideális adatainkat egy grafikon segítségével.

<details>
    <summary>Grafikonok</summary>
    <img src="https://github.com/user-attachments/assets/ef335ccb-3146-4c85-8a05-6fe4c8f8ebce" width="640" height="360">
    <img src="https://github.com/user-attachments/assets/5046d591-4af3-4afd-928e-c032efa1e49d" width="640" height="360">
</details>

Valamint méréseket végeztünk, miközben a polarizációt forgattuk. Ezeknek az adatait is kigyűjtöttük.

---

| Csillapítás (dB) | 60 | 60 | 60 | 60 | 60 | 60 | 60 |
|----------------|------|------|------|------|------|------|------|
| Mért bejövőszint (dBm) | -72,6 | -73,8 | -72,4 | -75,6 | -74,5 | -73,3 | -74,3 |
| Mért feszültség (V) | 0,54 | 0,37 | 0,16 | 0,11 | 0,40 | 0,43 | 0,47 |
| Leolvasott moduláció TX | 128QAM | 128QAM | 128QAM | 128QAM | 128QAM | 128QAM | 128QAM |
| Leolvasott moduláció RX | 64QAM | 64QAM | 64QAM | 64QAM | 64QAM | 64QAM | 64QAM |

---

Látható, hogy a feszültség csökkenése összefügg a bejövő jelszint változásaival. Mind két moduláció minden esetben tarjta az értékét, ami azt jelzi, hogy az adási moduláció stabilan tartja ezt a szintet. Összegzésként elmondható, hogy az adatok viszonylag stabil rendszert mutatnak, ahol a csillapítás állandó, de a bejövőszint és a feszültség enyhe változásokat mutat. Az adóoldali moduláció magasabb (128QAM), míg a vevőoldali alacsonyabb (64QAM), ami valószínűleg a csillapítás és a jelszint hatásának tudható be.

***5.4. Tápegység mérése:***

Miután a valós feladatunkat elvégeztük, kiváncsiság céljából megmértük, hogy a tápegységen mennyi áram folyik valamint milyen feszültség van rajta. 

<details>
    <summary>Mérés</summary>
    <img src="https://github.com/user-attachments/assets/d03a10cd-0fda-4888-be73-4e19c2258577" width="640" height="360">
</details>

**6. Összegzés:**



***6.1. Reflexió:***



---
