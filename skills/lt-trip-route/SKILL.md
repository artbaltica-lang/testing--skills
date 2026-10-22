---
name: lt-trip-route
description: Paruošia vienos krypties maršrutą tarp dviejų didžiųjų Lietuvos miestų autobuso ir traukinio paieškai. Naudok, kai reikia Vilniaus, Kauno, Klaipėdos, Šiaulių ar Panevėžio stotelių kodų ir datos, bet dar ne kainos.
---

# Maršruto kortelė

## Tikslas

Iš dviejų miestų ir datos paruošk maršruto kortelę tolesnei autobuso ir traukinio paieškai. Šis žingsnis kainų neima ir jų nelygina.

Miestai tik šie penki: Vilnius, Kaunas, Klaipėda, Šiauliai, Panevėžys. Kito miesto kodų nespėk. Jei abu miestai tie patys, sustok ir parašyk, kad maršrutas netinka.

Jei data nenurodyta, imk rytojaus dieną pagal `Europe/Vilnius`. Datos formatas `YYYY-MM-DD`.

## Stotelės

Traukinio stotelės paimtos iš `https://bilietas.ltglink.lt/api/stops/all`. Naudok tik šias pagrindines stoteles, ne gretimą stotelę tame pačiame mieste.

Autobuso kodai paimti iš `https://api.autobusubilietai.lt/api/route/search/by_slug/{slug}`. Vilnius turi du stotelių kodus, todėl jo kodas rašomas abu, atskyrus kableliu.

| Miestas | Traukinio stotelė | Traukinio ID | Autobuso kodas | Slug |
|---|---|---:|---|---|
| Vilnius | Vilnius | 17 | 2412-5,2412-1 | vilnius |
| Kaunas | Kaunas | 16 | 2408-1 | kaunas |
| Klaipėda | Klaipeda | 18 | 1474-1 | klaipeda |
| Šiauliai | Siauliai | 22 | 1641-1 | siauliai |
| Panevėžys | Panevezys | 182 | 1237-1 | panevezys |

Prieš atiduodamas kortelę patikrink abu šaltinius. Traukiniui rask Lietuvos stotelę, kurios `BusStopName` tiksliai sutampa su lentelės stotelės vardu. Autobusui atidaryk `https://api.autobusubilietai.lt/api/route/search/by_slug/{išvykimo-slug}-{atvykimo-slug}` ir palygink `origin.number` bei `destination.number` su lentele. Jei šaltinis neatsako arba kodas nesutampa, kortelės neatiduok ir kainų neieškok.

## Rezultatas

```text
Maršrutas: Vilnius → Kaunas
Data: 2026-10-23
Kryptis: viena, suaugęs keleivis
Traukinys: Vilnius (17) → Kaunas (16)
Autobusas: 2412-5,2412-1 → 2408-1
Kaina: šiame žingsnyje neimama
```

Miestų vardus rašyk lietuviškai. Rodyklių ir kodų nekeisk vietomis: pirma išvykimas, paskui atvykimas.
