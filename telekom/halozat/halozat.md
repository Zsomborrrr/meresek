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

Számomra konfiguráció tekintetében egy szimpla konfigot kell alkalmaznom a Layer 3 Switcheimen. A különösen kevésbé "alap" dolgokat az alábbiakban fogom felsorolni és mellékelni hozzájuk, hogy pontosan mit is csinálnak és, milyen parancsal kell őket életbe léptetni.

***5.3.2.1. Layer 2:***

***5.3.2.1.1. Rapid-pvst:***

- Gyorsabb konvergenciát biztosít: A klasszikus STP-hez (802.1D) képest a Rapid PVST gyorsabban reagál a hálózati változásokra (például ha egy link meghibásodik vagy visszatér).
- Minden VLAN-hoz külön Spanning Tree példányt futtat: Ez lehetővé teszi, hogy különböző VLAN-ok esetében más-más gyökérhíd (root bridge) és topológia legyen érvényben.
- Visszafelé kompatibilis az STP-vel: Ha olyan eszközzel találkozik, amely csak a hagyományos STP-t támogatja, akkor visszalassul, hogy kompatibilis maradjon.

```cisco
Access0(config)#spanning-tree mode rapid-pvst
```

***5.3.2.1.2. Bpduguard:***

A BPDU Guard egy fontos STP-védelmi mechanizmus, amely segít elkerülni a hurokképződést és a nem kívánt switch-csatlakozásokat azáltal, hogy tiltja azokat a portokat, amelyek váratlan BPDU-kat kapnak.

Ezt egy adott interface alá kell konfigurálnunk!

```cisco
Access0(config-if)#spanning-tree bpduguard enable
```

***5.3.2.1.3. Port-fast:***

- Átugorja az STP állapotokat: Normál esetben egy switch port az STP szerint Blocking → Listening → Learning → Forwarding állapotokon megy keresztül (~30 másodperc).
- PortFast-tal a port azonnal Forwarding állapotba lép, így nem kell várni az STP konvergenciára.
- Csak végponti eszközökre való: Ha egy switch másik switch-hez csatlakozik, nem szabad PortFast-ot használni, mert az STP nem tudná megfelelően kezelni a hurkokat.

Ezt egy adott interface alá kell konfigurálnunk!

```cisco
Access0(config-if)#spanning-tree portfast
```

***5.3.2.1.4. VTP mode transparent:***

- Nem vesz részt a VTP menedzsmentben: A switch nem fogadja el és nem alkalmazza más switch-ekről érkező VTP frissítéseket.
- Továbbítja a VTP üzeneteket: Ha a switch kap egy VTP üzenetet, akkor továbbküldi a trunk portokon keresztül, de maga nem módosítja a VLAN konfigurációját.
- Lokálisan kezeli a VLAN-okat: A VLAN-ok konfigurációja helyileg történik a switch-en, és ezek az információk nem frissülnek és nem terjednek más switch-ekre.
- Mentés NVRAM-ba: A VLAN konfigurációt elmenti az NVRAM-ba (vlan.dat fájl), míg a VTP client és server módok nem.

```cisco
Access0(config)#vtp mode transparent
```

***5.3.2.2. Security:***

***5.3.2.2.1. Port-security:***

- Beállítja a megengedett MAC-címek számát az adott interfészen.
- Ha több eszköz próbál csatlakozni, a switch a port biztonsági megsértéseként (violation) kezeli.
- Kombinálható más Port Security opciókkal, például a megsértés kezelésének módjával (violation mode).

Ezt egy adott interface alá kell konfigurálnunk!

```cisco
Access0(config-if)#switchport port-security maximum 1
Access0(config-if)#switchport port-security violation restrict
```

***5.3.2.2.2. DHCP Snooping:***

- Megakadályozza a hamis DHCP szerverek (rogue DHCP) működését, amelyek rossz IP-címeket osztogathatnának.
- Megkülönbözteti a megbízható ("trusted") és a nem megbízható ("untrusted") portokat:
- - Trusted (megbízható) portok: Csak itt engedélyezi a switch a DHCP szerver üzeneteket.
- - Untrusted (nem megbízható) portok: Nem engedi, hogy itt DHCP válaszok érkezzenek.
- DHCP Binding Table-t (snooping database) hoz létre: Tárolja a kliensek MAC-címét, IP-címét, interfészét és a bérleti időt, ezzel segítve a biztonsági funkciókat, például a Dynamic ARP Inspection-t (DAI) és az IP Source Guard-ot.

```cisco
Access0(config)#ip dhcp snooping
```

***5.3.2.2.3. ARP Inspection:***

- Ellenőrzi az ARP kéréseket és válaszokat, mielőtt azokat továbbítaná a hálózatban.
- Összeveti az ARP üzeneteket a DHCP Snooping Binding táblával – ha egy ARP csomag nem felel meg a tárolt IP-MAC hozzárendelésnek, akkor eldobja.
- Védelmet nyújt ARP mérgezéses (ARP Poisoning) támadások ellen, amelyekkel egy támadó átveheti más eszközök IP-címét és elterelheti a forgalmat.

```cisco
Access0(config)#ip arp inspection vlan 10
```

***5.3.2.2.4. AAA Radius Authentication:***

A AAA (Authentication, Authorization, and Accounting) egy biztonsági keretrendszer, amelyet hálózati eszközökön, például Cisco routereken és switch-eken használnak a felhasználók hitelesítésére, jogosultságainak kezelésére és tevékenységeik naplózására.

A RADIUS (Remote Authentication Dial-In User Service) egy protokoll, amelyet a AAA keretrendszerrel együtt használnak a központi felhasználó-hitelesítéshez és engedélyezéshez.

```cisco
Access0(config)#aaa new-model
Access0(config)#aaa authentication login default group radius local
Access0(config)#aaa authorization console
Access0(config)#aaa authorization exec default group radius local
```

***5.3.3. Teljes Access0 Konfiguráció***

Itt pedig, egy lenyíló fül segítségével, csatolom a teljes konfigurációt amely az Access0 switchen van rajta. A másik két switchen csupán bizonyos IP címek vannak átírva, egyébként teljesen megegyező konfigurációk vannak rajtuk.

<details>
    <summary>Access0 Konfiguráció</summary>

```plaintext
Building configuration...

Current configuration : 3729 bytes
!
! Last configuration change at 13:30:36 CET Thu Feb 20 2025 by zsombi
! NVRAM config last updated at 13:59:05 CET Thu Feb 20 2025 by andras
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
ip access-list standard LEGAL_HOSTS
 permit 0.0.0.0
 permit 172.16.0.0 0.0.0.63
 deny   any
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

**6. Összegzés:**

A vizsgálat célja egy teljes körű hálózati infrastruktúra megtervezése, konfigurálása és kivitelezése volt laboratóriumi környezetben. A feladat során a vizsgázó, részt vett a kábelezési folyamatokban, a hálózati eszközök (Cisco switchek és routerek) konfigurálásában, valamint a különböző hálózatbiztonsági és menedzsment beállítások elvégzésében.

A hálózat kiépítése során egy redundáns és biztonságos topológiát alkalmaztak, amelyben az Access Layer switchek konfigurálása volt a vizsgázó feladata. A beállítások során implementálta a Rapid-PVST protokollt a gyorsabb hálózati konvergencia érdekében, valamint olyan védelmi mechanizmusokat, mint a BPDU Guard és a Port Security. Továbbá, a DHCP Snooping és az ARP Inspection beállításokkal biztosította a hálózat védelmét a hamis DHCP szerverek és ARP mérgezéses támadások ellen.

A hálózati eszközök hitelesítésére és menedzselésére az AAA (Authentication, Authorization, Accounting) modellt és RADIUS szervert alkalmazták. Az IP címzési struktúra és a VLAN szegmentálás megfelelően lett kialakítva a különböző felhasználói csoportok számára. Az eszközök közötti kommunikáció és a konfigurációs beállítások helyességét a terminálon végzett parancsokkal ellenőrizték.

A projektmunka során a csapatmunka és a kommunikáció kulcsfontosságú volt az eszközök megfelelő beállításához és a hibák minimalizálásához. Az elkészült hálózat megfelelt a biztonsági és funkcionalitási követelményeknek, biztosítva a hatékony és stabil működést.

***6.1. Reflexió:***

A távközlési technikus vizsgafeladat teljesítése során rengeteg gyakorlati tapasztalatot szereztem, amely nagyban hozzájárult a szakmai fejlődésemhez. A feladat több lépcsőből állt, kezdve az egyszerű UTP kábel elkészítésétől egészen a stabil, redundáns és biztonságos hálózat megtervezéséig, konfigurálásáig és kivitelezéséig.

Pozitív élményként éltem meg, hogy sikeresen és hatékonyan tudtam együttműködni a csapattársaimmal. A feladatok felosztása és a kommunikáció gördülékenyen zajlott, így mindenki tisztában volt a saját felelősségével és feladataival. Kifejezetten elégedett vagyok azzal, hogy az Access Layer konfigurációját én végezhettem el, hiszen ez nagy felelősséggel járt, és lehetőséget biztosított arra, hogy mélyebben megismerjem a hálózati eszközök működését.

A konfiguráció során olyan fontos biztonsági és hálózatkezelési eljárásokat alkalmaztam, mint a Rapid-PVST, BPDU Guard, Port Security, DHCP Snooping és ARP Inspection. Ezek beállítása nemcsak a vizsgafeladat sikeres teljesítéséhez volt elengedhetetlen, hanem a valós hálózati környezetekben is kiemelten fontos szerepet játszanak.

Természetesen a feladat során kihívásokkal is szembesültem. Az egyik legnagyobb nehézséget a kábelkészítés pontos kivitelezése jelentette, mivel a megfelelő színsorrend betartása és a precíz csatlakozókészítés elengedhetetlen a hibamentes működéshez. Emellett a konfiguráció során előfordult néhány hiba, például egyes IP címek és VLAN beállítások nem megfelelő alkalmazása, amelyeket időben sikerült kijavítani a megfelelő teszteléssel és ellenőrzéssel.

Összességében elégedett vagyok a teljesítményemmel, mivel sikerült a vizsgafeladatot szakszerűen és pontosan végrehajtani. A megszerzett tudás és tapasztalatok hasznos alapot adnak a további szakmai fejlődésemhez, és megerősítették bennem azt a meggyőződést, hogy a távközlési hálózatok tervezése és konfigurálása területén szeretnék tovább fejlődni.