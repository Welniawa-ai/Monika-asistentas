# Skilsas: Pasiūlymai

## Kas tai

Padeda Monikai paruošti pasiūlymo turinį, kurį ji įkelia į Excel šabloną.
Pasiūlymas = dvi dalys: vizualinė lentelė (kairė) + kainų lapas (dešinė).

Excel'į pati pildys Monika (nuotraukos, spalvos, formatavimas).
Mano darbas: paruošti tekstą ir skaičius, kuriuos lengva nukopijuoti.

---

## Kaip naudoti

Pasakyk: **"Ruošiu pasiūlymą [kliento vardas]"** ir pateik:
1. Prekių sąrašą (gamintojas, prekės pavadinimas, matmenys jei žinomi)
2. Savikainą kiekvienai prekei
3. Ar taikoma 15% nuolaida, ar ne
4. Kambarių sekcijas (kokios patalpos)

Aš grąžinsiu:
- **Specifikacijas** — paruoštą tekstą "Pastabų" stulpeliui kiekvienai prekei
- **Kainų lentelę** — apskaičiuotus skaičius visiems stulpeliams
- **Lydrašti** — el. laiško tekstą klientui

---

## Pasiūlymo struktūra (iš Auželio pavyzdžio)

### Vizualinė dalis (Monika pildo Excel'yje)
| Eil. Nr. | Gamintojas | Prekė (nuotrauka) | Informacija | Pastabos |
|----------|-----------|-------------------|-------------|----------|
| — | spalvotas tekstas | nuotrauka + pavadinimas | variantas jei yra | techninė specifikacija |

**Kambario sekcijos:** Virtuvė/Svetainė → Koridorius → Drabužinė → Tėvų miegamasis → Vaiko miegamasis → Svečių kambarys → Vonia → Sporto salė

### Techninės specifikacijos šablonas (Pastabų stulpelis)
Standartiniai laukai pagal prekės tipą:
- **Baldai Sau / pagaminti:** Fasadai, Karkasas, Furnitūra (Blum), Stalčiai, Rankenėlės, Kabykla, kiti specifiniai
- **Minkštieji baldai (MBI):** Audinys (kaina/bėg.m), Gamybos terminas, Garantija
- **Importiniai (Poliform, Cattelan ir kt.):** Matmenys, Gamybos terminas, Garantija, Kilmės šalis
- **Čiužiniai (Manifattura faloma):** Modelis, Matmenys (AxPxI), Užvalkalas, Spiruoklės, Kietumas

### Kainų lapas
| Kiekis | Savikaina | Vnt. kaina | Vnt. kaina su nuolaida 15% | Suma |
|--------|-----------|------------|---------------------------|------|

**Nuolaidos logika:**
- Su nuolaida: `Vnt. kaina su nuolaida = Vnt. kaina × 0.85`
- Be nuolaidos: rašoma "Nuolaida netaikoma", suma = vnt. kaina
- Suma = Kiekis × Vnt. kaina su nuolaida (arba be nuolaidos)

**Apačioje:**
- Viso (be PVM): suma visų eilučių
- PVM (21%): Viso × 0.21
- VISO SU PVM: Viso + PVM

---

## Kainų skaičiavimo formulė

```
Vnt. kaina su nuolaida = ROUND(Vnt_kaina * 0.85, 2)
Suma eilutės = Kiekis * Vnt_kaina_su_nuolaida
PVM = ROUND(Viso * 0.21, 2)
Viso su PVM = Viso + PVM
```

---

## El. laiško šablonas (lydrašris klientui)

```
Tema: Pasiūlymas – [Kliento vardas/projektas]

Sveiki, [Vardas],

Siunčiame parengtą baldų ir interjero elementų pasiūlymą Jūsų projektui.

Pasiūlyme rasite:
• [kambario sekcijos, pvz. "Virtuvės, svetainės ir miegamojo baldus"]
• Kelių variantų pasiūlymus ten, kur galimos alternatyvos
• Gamybos terminus ir garantijos sąlygas

Jei turite klausimų ar norėtumėte aptarti bet kurį punktą — maloniai kviečiame susisiekti.

Pagarbiai,
Monika Kulinaitė
Kristinos Interjerai
```

---

## Pastabos

- Variantai žymimi: **Var. I**, **Var. II** (raudonai Excel'yje — tai Monika daro pati)
- Baldai Sau ir MBI — lietuviški gamintojai, trumpesni terminai
- Poliform, Cattelan Italia — italų importas, 7–13 sav. gamybos terminas
- Jei audinys nenustatytas — rašyti "audinius ir spalvas reikia patikslinti"
