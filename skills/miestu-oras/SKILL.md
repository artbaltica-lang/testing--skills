---
name: miestu-oras
description: Pateikia aktualią oro temperatūrą ir oro sąlygas penkiuose didžiausiuose Lietuvos miestuose, naudodamas oficialų Meteo.lt šaltinį. Naudok, kai prašoma Lietuvos miestų dabartinio oro, temperatūros ar trumpos orų suvestinės.
---

# Miestų oras

## Tikslas

Pateikti trumpą, aiškią penkių didžiausių Lietuvos miestų — Vilniaus, Kauno, Klaipėdos, Šiaulių ir Panevėžio — oro suvestinę: temperatūrą ir sąlygas. Duomenų šaltinis turi būti oficialus Lietuvos hidrometeorologijos tarnybos portalas **Meteo.lt** arba jo vieša API.

## Darbo eiga

1. Gauk dabartinę datą, laiką ir Lietuvos vietos laiko juostą, kad galėtum parinkti artimiausią aktualų prognozės įrašą.
2. Pirmiausia naudok oficialų Meteo.lt API:
   - API dokumentacija: https://api.meteo.lt/
   - Kiekvieno miesto ilgalaikės prognozės adresas:
     - Vilnius: `https://api.meteo.lt/v1/places/vilnius/forecasts/long-term`
     - Kaunas: `https://api.meteo.lt/v1/places/kaunas/forecasts/long-term`
     - Klaipėda: `https://api.meteo.lt/v1/places/klaipeda/forecasts/long-term`
     - Šiauliai: `https://api.meteo.lt/v1/places/siauliai/forecasts/long-term`
     - Panevėžys: `https://api.meteo.lt/v1/places/panevezys/forecasts/long-term`
3. Jei API pasiekti nepavyksta, atidaryk oficialų puslapį https://www.meteo.lt/prognozes/lietuvos-miestai/ ir pasirink kiekvieną iš penkių miestų. Nenaudok neoficialių šaltinių kaip pakaitalo, nebent aiškiai pažymėtum, kad oficialus šaltinis nepasiekiamas.
4. Kiekvienam miestui rask prognozės įrašą, kurio laikas yra artimiausias dabartiniam Lietuvos laikui. Patikrink laiko žymą ir nevadink ateities prognozės dabartiniu stebėjimu.
5. Ištrauk temperatūrą Celsijaus laipsniais ir orų sąlygų aprašą. Jei API grąžina tik `conditionCode`, išversk jį į sąlygų pavadinimą tik pagal oficialų Meteo.lt aprašą ar dokumentaciją; niekada neatspėk reikšmės vien iš kodo. Jei sąlygų aprašymo patikimai nustatyti nepavyksta, parašyk „sąlygų aprašas neprieinamas“.
6. Patikrink, ar pateikti duomenys yra visiems penkiems miestams ir ar temperatūros bei sąlygos turi galiojančias reikšmes. Jei miesto duomenų nėra, pažymėk tai atskirai; neišgalvok trūkstamų reikšmių.
7. Nurodyk duomenų gavimo laiką Lietuvos laiku, šaltinį ir tiesioginę nuorodą į Meteo.lt.

## Atsakymo formatas

Atsakyk lietuvių kalba. Pateik lentelę:

| Miestas | Temperatūra | Oro sąlygos | Prognozės laikas |
|---|---:|---|---|

Po lentele pridėk:
- **Duomenų atnaujinimo / patikrinimo laikas:** Lietuvos laiku.
- **Šaltinis:** Meteo.lt su nuoroda.
- Trumpą pastabą, jei bent vieno miesto duomenys nepasiekiami arba tai yra prognozė, o ne tiesioginis stoties matavimas.

Laikyk atsakymą glaustą. Nerodyk visos savaitės prognozės, jei vartotojas prašo tik temperatūros ir sąlygų.

## Patikimumas ir apribojimai

- Naudok tik patikrintus, ką tik gautus duomenis; niekada nepateik iš atminties temperatūrų kaip dabartinių.
- Jei svetainė arba API neveikia, aiškiai nurodyk, kad nepavyko gauti naujausių duomenų.
- Atskirai atskirk prognozę nuo išmatuoto stebėjimo.
- Neperkrauk API užklausomis. Viena užklausa kiekvienam miestui yra pakankama.
- Nurodyk Meteo.lt kaip duomenų šaltinį ir laikykis jo duomenų naudojimo sąlygų.
