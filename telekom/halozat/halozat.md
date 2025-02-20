**MÉRÉSI JEGYZŐKÖNYV**

**Távközlési technikus vizsgafeladat**  
**Komplex hálózat tervezése, konfiguráláse és kivitelezése**

---

**1. Mérés helye és időpontja:**  
- Helyszín: Telekom Labor
- Dátum: 2025.02.13.


**2. A vizsgázó neve:**  
- Név: Sándor Zsombor

**3. Feladat leírása:**

A feladat során, a legalapabbaktól kezdve, hogy sima UTP kábelt készítünk, egészen egy stabil, redundás és biztonságos hálózat megtervezését, konfigurálását és kivitelezését visszük végbe, labor körülmények között.

**4. Szükséges eszközök:**  

***4.1. Kábelszerelés:***  

- 2db RJ45
- 2db UTP törésgátló
- Oldalcsípő
- Krimpelő fogó
- Blankoló
- FLUKE networks LinkRunner AT 2000
- CAT5 UTP kábel

***4.2. Hálózat felépítés:***  

- 5db Cisco Catalyst 3560 Series PoE-8 Layer 3 Switch
- 12db Ethernet kábel
- Cisco 800 Series SOHO Router

**5. Konfiguráció, mérés, tesztelés:**

***5.1. Kábelszerelés:***

Ehhez a folyamathoz szükségünk van, kábelenkét 2db RJ45-ös csatlakozóra, valamint szintén kábelenkét 2db UTP törésgátlóra. Mind ezek mellett kell nekünk oldalcsípő és krimpelő fogó. Az ethernet kábel elkészítéséhez, a klasszikus és egyszerű valamint jól bevált színsorrendet fogjuk használni.

<details>
    <summary>Színsorrend</summary>
    <img src="https://github.com/user-attachments/assets/216409ef-4bb6-476a-b89a-dd5b416ae270" width="360" height="640">
</details>

Első sorban eltávolítjuk a külső műanyag/gumi védőréteget a kábel kezelésbe vett oldaláról. Majd utána ráhúzzuk a kábelünkre a törésgátló gumi borítást.

<details>
    <summary>Blankolt kábel</summary>
    <img src="https://github.com/user-attachments/assets/cbaa954a-17e6-4e7c-b5ae-bec148b9ac7f" width="360" height="640">
</details>

Ezek után a csavart érpárokat, kicsavarjuk, kiegyenesítjük és megfelelő sorrendbe rendezzük őket. Majd ha ezekkel elkészültünk, levágjuk a felesleges vezetékeket, így hagyva egy kb 1 centi hosszú sorrendbe helyezett kábelvéget.

<details>
    <summary>Sorbarendezett</summary>
    <img src="https://github.com/user-attachments/assets/a9ffc243-60ba-4d70-aa1d-0a2de4e70f36" width="360" height="640">
</details>

Ha megfelelő hosszúságú, és rendezett színsorrendbe vannak a vezetékek, akkor ráhelyezzük az RJ45-ös csatlakozót, megfelelő oda figyeléssel, így minden kis vékony vezeték, a saját sávjában fog kikötni. Ezt sikeresen elvégezve a krimpelővel rároppatjuk a csatlakozót a kábelre, és ráhúzzuk az előlegesen felhelyezett törésgátlót.

<details>
    <summary>Kész kábel</summary>
    <img src="https://github.com/user-attachments/assets/09211634-135a-459d-affc-dcbd2ac05fcd" width="360" height="640">
</details>

Amint meg vagyunk az egyik oldallal, ugyan ezekkel a lépésekkel elkészítjük a másik oldalát is a kábelnek. Majd ha végeztünk, akkor az egyik végét bedugjuk egy switchbe, a másik végét pedig az UTP teszterbe, és a műszerben a SWITCH opciót választva, megmondja nekünk, hogy megfelelő-e az összeköttetés, vagy pedig elrontottunk valamit.

<details>
    <summary>Teszter</summary>
    <img src="https://github.com/user-attachments/assets/64f4eb76-f813-4ffa-b879-cd81746be134" width="360" height="640">
</details>

Ha mindent rendben talált a műszer, akkor a kábelt sikeresen elkészítettük.

***5.2. Hálózat topológiai ábrája megbeszélések alapján:***

<details>
    <summary>Topológia</summary>
    <img src="https://github.com/user-attachments/assets/98755eef-a655-4d52-9f80-30c2c3c96641" width="302" height="360">
</details>


***5.3. Topológia & Konfiguráció:***

***5.3.1. Topológia kiépítése:***

Labortársaimmal, megbeszélést követően felosztottuk, hogy a hálózatban melyik eszközt Ki fogja konfigurálni és használni. A döntés során,  úgy alakult, hogy Én fogom kezelni az Access Layert amely a felhasználókhoz legközelebb lévő szint, hálózati tekintetből. 3 db eszközt fogok kezelni a projektmunka során.

<details>
    <summary>Access Switchek</summary>
    <img src="https://github.com/user-attachments/assets/2486695b-80f9-4d10-811a-370038d47121" width="640" height="360">
</details>

Miután eszközeimet elrendeztem, elkezdhettük összekötni őket a Distribution Layer-el. Itt szintén fontos a Társaimmal való kommunikáció, hogy pontosan melyik Ethernet kábel, az adott Switchbe/Routerbe melyik portra csatlakozik. 

<details>
    <summary>Összekötött Access Switchek</summary>
    <img src="https://github.com/user-attachments/assets/28a192c9-7239-4b3f-bbf6-28066a0f75d3" width="640" height="360">
</details>

Amint összekötöttük egymást, annak helyességét a konfig felületen tudjuk ellenőrizni az alábbi parancsal:

```cisco
Access0(config)#do show cdp neighbors
```

A terminálon belüli ellenőrzést az Access0 switchen végeztem az alábbi sorokban, azonban minden eszközön meg kell ismételni az ellenőrzést.

```cisco
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone,
                  D - Remote, C - CVTA, M - Two-port Mac Relay

Device ID        Local Intrfce     Holdtme    Capability  Platform  Port ID
Distribution0.Telekom.Intra
                 Fas 0/1           142             R S I  WS-C3560- Fas 0/3
Distribution1.Telekom.intra
                 Fas 0/2           167             R S I  WS-C3560- Fas 0/3
```

***5.3.2. Konfiguráció:***

Konfiguráció tekintetében az IP cím tartományokkal kapcsolatban az alábbiakban mutatva egyeztünk meg.

- Management (Loopback): 10.0.0.X /32
- Uplink: 192.168.254.X /30
- Access0
-- Users (Vlan10): 172.16.0.0 /26
- Access1
-- Users (Vlan10): 172.16.0.64 /26
- Access2
-- Users (Vlan10): 172.16.0.128 /26

Számomra konfiguráció tekintetében egy szimpla konfigot kell alkalmaznom a Layer 3 Switcheimen.

<details>
    <summary>Access0 Konfiguráció</summary>

```plaintext
Building configuration...

Current configuration : 3764 bytes
!
! Last configuration change at 13:14:23 CET Thu Feb 20 2025 by zsombi
! NVRAM config last updated at 13:29:47 CET Thu Feb 20 2025 by zsombi
!
version 15.0
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
service password-encryption
!
hostname Access0
!
boot-start-marker
boot-end-marker
!
!
no logging console
no logging monitor
enable secret 5 $1$HuBF$0Qc1ooDS/Efcxej/hl1mA/
!
username admin secret 5 $1$IXLf$7tAbYb0TEYUiE1T6bCqaq.
aaa new-model
!
!
aaa authentication login default group radius local
aaa authorization console
aaa authorization exec default group radius local
!
!
!
!
!
!
aaa session-id common
clock timezone CET 1 0
clock summer-time CEST recurring last Sun Mar 2:00 last Sun Oct 3:00
system mtu routing 1500
vtp mode transparent
ip routing
ip arp inspection vlan 10
ip domain-name Telekom.Intra
!
!
!
ip dhcp snooping vlan 10
ip dhcp snooping
!
!
!
!
!
!
!
!
!
spanning-tree mode rapid-pvst
spanning-tree extend system-id
!
vlan internal allocation policy ascending
!
vlan 10
 name Users
!
ip ssh version 2
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Loopback0
 ip address 10.0.0.1 255.255.255.255
 ip ospf 1 area 0
!
interface FastEthernet0/1
 no switchport
 ip address 192.168.254.65 255.255.255.252
 ip ospf network point-to-point
 ip ospf 1 area 0
!
interface FastEthernet0/2
 no switchport
 ip address 192.168.254.69 255.255.255.252
 ip ospf network point-to-point
 ip ospf 1 area 0
!
interface FastEthernet0/3
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security violation restrict
 switchport port-security
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/4
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security violation restrict
 switchport port-security
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/5
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security violation restrict
 switchport port-security
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/6
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security violation restrict
 switchport port-security
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/7
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security violation restrict
 switchport port-security
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/8
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security violation restrict
 switchport port-security
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface GigabitEthernet0/1
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan10
 ip address 172.16.0.1 255.255.255.192
 ip access-group LEGAL_HOSTS in
 ip helper-address 10.0.1.2
 ip ospf 1 area 0
!
router ospf 1
 passive-interface Vlan10
 passive-interface Loopback0
!
no ip http server
no ip http secure-server
!
!
!
ip access-list standard LEGAL_HOST
 deny   any
ip access-list standard LEGAL_HOSTS
 permit 0.0.0.0
 permit 172.16.0.0 0.0.0.63
ip access-list standard REMOTE_CLI
 permit 10.0.1.2
 deny   any
!
ip radius source-interface Loopback0
logging source-interface Loopback0
logging host 10.0.1.2
!
!
!
radius server radius
 address ipv4 10.0.1.2 auth-port 1812 acct-port 1813
 key 7 011B03085704575D72
!
!
!
vstack
!
line con 0
line vty 0 4
 access-class REMOTE_CLI in
 transport input ssh
line vty 5 15
 access-class REMOTE_CLI in
 transport input ssh
!
ntp source Loopback0
ntp server 10.0.1.2
end


```
</details>

***5.3. Kábel szerelés:***


**6. Összegzés:**

***6.1. Reflexió:***
