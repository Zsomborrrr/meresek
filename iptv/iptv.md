**MÉRÉSI JEGYZŐKÖNYV**

**Távkozlelési technikus vizsgafeladat**  
**B tétel: DVB-T jel fejállomásba küldése és IPTV rendszeren való kiadása**

---

**1. Mérés helye és időpontja:**  
- Helyszín: Villamos 3 labor
- Dátum: 2025.02.05.


**2. A vizsgázó neve:**  
- Név: Sándor Zsombor

**3. Sükséges eszközök:**  
- Antenna: Iskra P2845
- Fejállomás: LEMCO SCL-824CT
- Set-top box: MAG IPTV
- Router: IGMP protokollt támogató és DHCP képes router (Asus router)
- Mérőműszer: METEK HDD digitális TV jelmérő
- Kábelezés: Koaxiális és UTP kábelek

**4. Mérések és beállítások:**

### **4.1 Antenna beállítás**
- Kiválasztott antenna típusának kiválasztásánál, egy kültéri antennára esett a választás.
- Rögzítés módja: Antenna álvány
- Adótorony: Miskolc, Avasi adótorony
- Antenna iránya: Horizontális Dél-Nyugat 233fok
- A miskolc városi tvre hangoljuk az adást mert ez adja a leggyengébb jelet és ha ez jó az összestöbbi is jó lesz.

### **4.2 Jelszintmérés az antennánál**
| Paraméter | Érték |
|------------|---------|
| Jelerősség (dBμV) | 38.1 |
| Modulation Error Ratio (MER - dB) | 16.7 |
| Polarizáció | Horizontális 

### **4.3 Fejállomás konfiguráció**
- Input1 - Multiplex B, ch35
- Input2 - Miskolci Városi TV, ch41
- Input3 - Multiplex A, ch45
- Input4 - Multiplex E, ch48

- Lemco ip - 192.168.1.200
- Lemco login - admin 12345
- Lemco iptv stream - 239.1.1.1-39

### **4.4 Router rendszer beállítás**
- Router elérése - 192.168.50.1 --> 192.168.1.1
- Router login - admin admin12345678
- Router ssid psswrd - iptv 12345678
- Router lan iptv proxy - 8888
- Letöltési fel/sebesség - 93.46Mbps

- Lan 1 - lemco control 1Gbps
- Lan 2 - üres
- Lan 3 - lemco ip stream 1Gbps
- Lan 4 - set top box 100Mbps

- VLC elérési cím: http://192.168.1.1:8888/udp/239.1.1.1:1234

### **4.5 IPTV stream ellenőrzése**


---


