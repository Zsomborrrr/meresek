**MÉRÉSI JEGYZŐKÖNYV**  
**Távkozlési Technikus Vizsgafeladat**  

**Vizsgázó neve:** Sándor Zsombor
**Dátum:** 2025.01.29.
**Helyszín:** Labor 
**Vizsgabizottság tagjai:** Sándor Péter  

---

## **1. Előkészítés és Tervezés**

### **1.1. Eszközök gyári visszaállítása**

- **Mikrotik LHG18 LTE antenna:** Gyári visszaállítás sikeres.
- **Mikrotik nRay 60GHz antennák:** Mindkét eszköz visszaállítása sikeres.
- **SOHO router:** Gyári visszaállítás elvégezve.

### **1.2. Hálózati topológia tervezése**

- Hálózati diagram elkészítve.
- IP-címek megfelelő kiosztása megtörtént.

---

## **2. Eszközök Telepítése és Konfigurálása**

### **2.1. Mikrotik LHG18 LTE antenna beállítása**

- Antenna elérhetősége: **http://192.168.188.1**
- IP-cím beállítva: **192.168.88.1**
- DHCP szerver beállítva.
- Kapott nyilvános IP-cím: **10.169.251.191**
- Jelerősségi paraméterek:
  - **RSRP:** -81 dBm
  - **RSRQ:** -10 dB
  - **SINR:** -18 dB
  - **RSSI:** -54 dBm

### **2.2. Mikrotik nRay 60GHz antennapár beállítása**

- **Master antenna (192.168.88.2)**
- **Slave antenna (192.168.88.3)**
- Kapcsolat létrejött.
- **Jelminőségi paraméterek:**
  - Kapcsolat erőssége: [érték]

### **2.3. SOHO router beállítása AP módban**

- Router IP-címe: **192.168.88.4**
- WiFi SSID: **GazdaXX**
- WiFi jelszó: **G1234567**
- AP mód beállítva.

---

## **3. Hálózati Tesztelés és Hibakeresés**

### **3.1. Ping tesztek**

- **Ping eredmények:**
  - **192.168.88.1:** [ms]
  - **192.168.88.2:** [ms]
  - **192.168.88.3:** [ms]
  - **192.168.88.4:** [ms]
- Csomagvesztés nem tapasztalható.

### **3.2. Sávszélesség mérése (iperf)**

- **Szerver oldali teszt:**  
  - Parancs: `iperf3 -s`

- **Kliens oldali teszt:**  
  - Parancs: `iperf3 -c 192.168.88.xxx`
  - Mérési eredmények (Mbps): **[eredmény]**

- **Hálózati felderítés engedélyezve.**

- **Speedtest eredmény:**  
  - Letöltési sebesség: **[Mbps]**
  - Feltöltési sebesség: **[Mbps]**
  - Ping: **[ms]**

---

## **4. Dokumentáció és Értékelés**

- Hálózati forgalom monitorozása elvégezve.
- Hibakeresés dokumentálva.
- Dokumentáció összegzése:
  - **Hálózati topológia:** [Melléklet]
  - **Beállítások:** [Részletek]
  - **Teszt eredmények:** [Melléklet]

---

**Végső értékelés:**
- **Pontszám:** [ /100]
- **Megjegyzések:**

**Aláírások:**  
Vizsgázó: __________________  
Vizsgabizottság: __________________  

---


