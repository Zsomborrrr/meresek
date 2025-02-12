**MÉRÉSI JEGYZŐKÖNYV**

**Távkozlelési technikus vizsgafeladat**  
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

***5.2. Hálózat összekötése, topológiai ábra alapján:***

<details>
    <summary>Topológia</summary>
    <img src="https://github.com/user-attachments/assets/98755eef-a655-4d52-9f80-30c2c3c96641" width="302" height="360">
</details>


***5.3. Konfiguráció:***


***5.4. Kábel szerelés:***


***5.5. Kábel szerelés:***


***5.6. Kábel szerelés:***


**6. Összegzés:**

***6.1. Reflexió:***
