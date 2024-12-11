## Mérési Jegyzőkönyv


**Mérési Feladat:**
A különböző bitsebességek hatásának vizsgálata a jelminőségre.

**Cél:**
A Johansson 8202 DVB-T modulátor többcsatornás képességeinek megismerése, valamint a bitsebesség és a jelminőség közötti kapcsolat vizsgálata.

**Feladatok:**

1. Két program (TV1 és TV2) beállítása és mérésük különböző bitsebességek mellett.
2. Jelminőségi paraméterek (jelszint, MER) mérése különböző bitsebességi beállítások esetén.

---

**Mérési Eszközök:**

- 2 db Johansson 8202 DVB-T modulátor
- DVB-T vevő (TV vagy mérőműszer)
- RF kábelek
- METEK HD spektrum/jelszint analizátor
- Laptop a jegyzőkönyv készítéséhez

---

**Mérési Paraméterek:**

- **Modulátor konfiguráció:**

  - Gyári beállítások visszaállítása (Factory Reset).
  - Két RF frekvencia beállítása: 674 MHz és 682 MHz.
  - Többcsatornás jelkimenet beállítása két programmal (TV1 és TV2).
  - Moduláció: 64-QAM
  - Sávszélesség: 8 MHz
  - Bitsebességi beállítások kezdetben:
    - TV1: 15 Mbps
    - TV2: 10 Mbps

- **Mérési lépések:**

  - Jelszint mérése (dBm).
  - Modulation Error Ratio (MER) mérése (dB).
  - Bitsebességek mérése.
  - TV2 bitsebességének fokozatos növelése 10 Mbps-tól a maximális értékig, és a jelszint, MER és vevőreakció ismélt ellenőrzése.

---

**Mérési Eredmények:**

| Mérési Paraméter | RF frekvencia (MHz) | Program neve | Bitsebesség (Mbps) | Jelszint (dBm) | MER érték (dB) |
| ---------------- | ------------------- | ------------ | ------------------ | -------------- | -------------- |
| Mérés 1          | 674                 | TV1          | 15                 | -23.6          | 34.5           |
| Mérés 2          | 682                 | TV2          | 10                 | -21.8          | 39.8           |
| Mérés 3          | 682                 | TV2          | Max                | -22.3          | 38.6           |

---
**Képek a méréskhez**
<details>
  <summary>TV1</summary>
    <details>
      <summary>TV</summary>
      <img src="https://github.com/user-attachments/assets/6434e11e-c51d-4914-9af4-0e1055eaf317">
    </details>
    <details>
       <summary>Spect</summary>
      <img src="https://github.com/user-attachments/assets/7991c104-cb53-4137-88d8-1928b98bb752">
    </details>
    <details>
      <summary>Meter</summary>
      <img src="https://github.com/user-attachments/assets/01179ba0-5c07-4152-a648-26fcaac11a1e">
    </details>
</details>

<details>
  <summary>TV2</summary>
    <details>
      <summary>TV</summary>
      <img src="https://github.com/user-attachments/assets/d627744e-eaff-4312-847e-e9d84b39c80b">
    </details>
    <details>
       <summary>Spect</summary>
      <img src="https://github.com/user-attachments/assets/2a9ea7e5-b65f-484e-bea9-c60b098a2dd2">
    </details>
    <details>
      <summary>Meter</summary>
      <img src="https://github.com/user-attachments/assets/23c92924-1d79-4c9f-9c60-94dcac9c2c00">
    </details>
</details>

<details>
  <summary>TV2 emelt bitráta</summary>
    <details>
      <summary>TV</summary>
      <img src="https://github.com/user-attachments/assets/6b281ed9-2002-4802-97ea-a4e6c462424f">
    </details>
    <details>
       <summary>Spect</summary>
      <img src="https://github.com/user-attachments/assets/04958cd2-891e-4f7e-a9d5-cee12bb6fe73">
    </details>
    <details>
      <summary>Meter</summary>
      <img src="https://github.com/user-attachments/assets/a9764102-0efb-411e-9485-2629344bf0c1">
    </details>
</details>
---

**Megjegyzések:**

- A bitsebesség növelése során észlelt jelenségek:
  - A jelszint és MER érték közötti összefüggések.
  - A DVB-T vevő viselkedése magasabb bitsebességek mellett.

---

**Következtetések:**

1. A mérések eredményei alapján megállapítható, hogy a bitsebesség növelése milyen mértékben befolyásolja a jelminőséget (MER).
2. A legjobb jelminőséget biztosító beállítások azonosítása mindkét program számára.

---

**Javaslatok a További Mérésekhez:**

- A különböző modulációs típusok és sávszélességi beállítások vizsgálata.
- Az RF frekvenciák közötti interferencia elemzése.

**Készítette:**
(2024.12.11., Sándor Zsombor)
