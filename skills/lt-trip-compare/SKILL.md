---
name: lt-trip-compare
description: Palygina autobuso ir traukinio bilieto kainą vienai krypčiai tarp dviejų didžiųjų Lietuvos miestų. Naudok, kai prašoma pigiausio kelionės varianto tarp Vilniaus, Kauno, Klaipėdos, Šiaulių ar Panevėžio. Šis workflow iš eilės paleidžia maršruto, autobuso ir traukinio žingsnius.
---

# Kelionės kainos palyginimas

## Tikslas

Vienu paleidimu atlik tris žingsnius ta pačia tvarka ir tik po jų palygink kainas. Žingsnių nekeisk vietomis ir nepraleisk.

1. Perskaityk `skills/lt-trip-route/SKILL.md` ir paruošk maršruto kortelę. Jei kortelė neparuošta, sustok. Kainų šiame žingsnyje nėra.
2. Perskaityk `skills/lt-bus-price/SKILL.md` ir paimk autobuso kainą pagal tą pačią kortelę.
3. Perskaityk `skills/lt-train-price/SKILL.md` ir paimk traukinio kainą pagal tą pačią kortelę.
4. Tik tada sudėk abi kainas į vieną lentelę.

Autobuso kainos neimk iš traukinio atsakymo ir atvirkščiai. Jei vienas šaltinis neatsako, kito kainą vis tiek parodyk, o trūkstamą langelį užpildyk „nėra“.

## Palyginimas

Abu skaičiai turi būti eurais už vieną suaugusį keleivį, vieną kryptį, kortelės dieną.

- Jei yra abi kainos, pigesnis yra tas, kurio suma mažesnė. Jei sumos lygios, rašyk „kaina vienoda“.
- Jei bent vienos kainos nėra, nerašyk, kuris variantas pigesnis.

## Rezultatas

```text
Maršrutas: {miestas} → {miestas}
Data: {YYYY-MM-DD}

Transportas | Išvykimas | Atvykimas | Kaina
Autobusas | {laikas} | {laikas} | {kaina} EUR
Traukinys | {laikas} | {laikas} | {kaina} EUR

Pigesnis: {autobusas arba traukinys}
```

Po lentele pridėk abu šaltinius: `https://www.autobusubilietai.lt/` ir `https://bilietas.ltglink.lt/`. Autobuso eilutėje palik ir maršruto pavadinimą iš autobuso atsakymo, jei jame yra daugiau miestų nei prašyta pora.
