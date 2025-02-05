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
- Mérőműszer: METEK HDD
- Kábelezés: Koaxiális és UTP kábelek

**4. Mérések és beállítások:**

### **4.1 Antenna beállítás**
- Kiválasztott antenna típusának kiválasztásánál, egy kültéri antennára esett a választás.
- Rögzítés módja: Antenna álvány
- Adótorony: Miskolc, Avasi adótorony
- Antenna iránya: Horizontális Dél-Nyugat 233fok
- A miskolc városi TVre hangoljuk az adást mert ez adja a leggyengébb jelet és ha ez jó az összestöbbi is jó lesz.

### **4.2 Jelszintmérés az antennánál**
| Paraméter | Érték |
|------------|---------|
| Jelerősség (dBμV) | 38.1 |
| Modulation Error Ratio (MER - dB) | 16.7 |
| Polarizáció | Horizontális 

- Lock állapot aktív.

#### **Mérési képek:**

<details>
    <summary>Spektrum</summary>
    <img src="https://github.com/user-attachments/assets/5fbf7610-f070-4dfc-b502-3c9d7abe81b8" width="640" height="360">
</details>
<details>
    <summary>TV</summary>
    <img src="https://github.com/user-attachments/assets/ac667c96-8e30-4460-8efd-867a3bbb25e6" width="640" height="360">
</details>
<details>
    <summary>Meter</summary>
    <img src="https://github.com/user-attachments/assets/17246ed4-1af6-44ec-9e7f-cd822794d85f" width="640" height="360">
</details>


### **4.3 Fejállomás konfiguráció**
- Input1 - Multiplex B, ch35
- Input2 - Miskolci Városi TV, ch41
- Input3 - Multiplex A, ch45
- Input4 - Multiplex E, ch48

#### **Adat képek:**
<details>
    <summary>Lemco Portok</summary>
    <img src="https://github.com/user-attachments/assets/db7434d3-1634-4cc4-8a22-19d67e99b072" width="640" height="360">
    <img src="https://github.com/user-attachments/assets/31428b5b-1575-438d-92c2-0be50296328c" width="360" height="640">
</details>
<details>
    <summary>Miskolci adók</summary>
    <img src="https://github.com/user-attachments/assets/02311e84-efb3-426e-82f4-5ee4a8d62bd5" width="640" height="360">
</details>


- Lemco ip - 192.168.1.200
- Lemco login - admin 12345
- Lemco iptv stream - 239.1.1.1-39

<details>
    <summary>IPTV kiosztás</summary>
    <img src="https://github.com/user-attachments/assets/81f86454-ac1f-48c8-96e7-0df82be1ad32" width="640" height="360">
</details>

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

### **4.5 IPTV Stream és Multicast konfigurálás**
- Multicast IP tartomány: 239.1.1.1-39
- Multicast port: 1234

#### **Képek:**
<details>
    <summary>Leterheltség</summary>
    <img src="https://github.com/user-attachments/assets/f66f37ce-80c0-46b0-acb5-818d8febd2db" width="640" height="360">
</details>

### **4.6 IPTV stream ellenőrzése**

#### **Képek:**
<details>
    <summary>CMD mérés</summary>
    <img src="https://github.com/user-attachments/assets/c7409d28-7263-465e-b638-aa9c0c147d36" width="640" height="540">
</details>
<details>
    <summary>Vlc adatok</summary>
    <img src="https://github.com/user-attachments/assets/bdd7856a-58e8-46ac-a85f-474bd7809db5" width="360" height="640">
    <img src="https://github.com/user-attachments/assets/9e6321ef-ed26-4288-838b-f66275b24c82" width="360" height="640">
</details>


### **Összegzés:**
Miután összeszereltük a hálózatot a megfelelő kábeleket használva, majd első sorban a routert aztán a fejállomást is bekonfiguráltuk, ezek után rátérhettünk a Set Top Box beállítására. Mikor befejeztük az összes eszköz testreszabását, a STB-re HDMI kábellel csatlakoztatott monitor segítségével láthattuk, hogy jól működik a hálózatunk. Ezek után a labortásaim segítségével ellenőriztük, hogy Ők is képesek venni az adást a VLC segítségével. A feladat elvégézést sikeresnek tekintem.


---


