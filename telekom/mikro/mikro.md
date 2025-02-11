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

***5.1 összekötés:***
Első sorban a beltéri egységeinket a tápegységgel összekötöttük és bekapcsoltuk azokat. 
Majd ezek után koax kábellel összekötöttük a mikrókat a beltéri eszközökkel.
Mind ezekmellett duplex összeköttetést használtunk.
A laptopot DHCP-be állítottuk, és Ethernet kábellel az eszköz LCT portjára csatlakoztunk.
Majd egy webböngészővel beléptünk a konfigurációs felületre az alábbi IP segítségével: 
http://172.17.254.253

Melyhez a belépéshez szükséges adatotak a gyártó adja nekünk meg. 
Felhasználónév: Admin
Jelszó: 12345678

***5.2 konfigurálás:***
Ahhoz, hogy legyen rádiós összekötettésünk, az alap rádiós paramétereket be kellett állítani.
- Channel Spacing: 28 MHz
- Referenc Modulation: QPSK
- TX Frekvencia: 25808 MHz
- TX Power Control: MTPC (Manual Transmission Power Control) 
Ha ez nincs beállítva akkor automatikusan növeli az adót és emiatt nem tudunk a csillapítással mérni.
- TX Power: 0 dBm (1 mW)
- AMR moduláció: QPSK, 16QAM, 32QAM, 64QAM, 128QAM, 256QAM
Ezzel állítottuk be, hogy QPSK és 256QAM között bármilyen modulációt felvehet, annak érdekében, hogy ne szakadjon meg.

***5.3 valami:***


***5.4 valami:***


***5.5 valami:***


***5.6 valami:***


***5.7 valami:***


 **6. Összegzés:**


---