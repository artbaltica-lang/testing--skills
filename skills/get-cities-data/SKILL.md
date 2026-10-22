---
name: get-cities-data
description: Surenka penkių didžiausių Lietuvos miestų meteorologinius duomenis iš Meteo.lt ir pateikia juos vienoje lentelėje. Naudok, kai prašoma ne tik temperatūros, bet ir vėjo, drėgmės, slėgio, debesuotumo, kritulių ar kitų Meteo.lt prognozės laukų.
---

# Miestų meteorologiniai duomenys

## Tikslas

Pateikti vieną lentelę su Vilniaus, Kauno, Klaipėdos, Šiaulių ir Panevėžio artimiausios prognozės duomenimis. Šaltinis yra oficialus Meteo.lt API. Temperatūra yra tik vienas stulpelis. Kiti stulpeliai imami iš to paties prognozės įrašo.

## Darbo eiga

1. Nustatyk dabartinį Lietuvos laiką.
2. Kiekvienam miestui atlik vieną užklausą:
   - Vilnius: `https://api.meteo.lt/v1/places/vilnius/forecasts/long-term`
   - Kaunas: `https://api.meteo.lt/v1/places/kaunas/forecasts/long-term`
   - Klaipėda: `https://api.meteo.lt/v1/places/klaipeda/forecasts/long-term`
   - Šiauliai: `https://api.meteo.lt/v1/places/siauliai/forecasts/long-term`
   - Panevėžys: `https://api.meteo.lt/v1/places/panevezys/forecasts/long-term`
3. Iš `forecastTimestamps` pasirink įrašą, kurio `forecastTimeUtc` artimiausias dabartiniam Lietuvos laikui. Užsirašyk `forecastType` ir `forecastCreationTimeUtc`.
4. Iš to įrašo imk tik esamus laukus:
   - `airTemperature`
   - `feelsLikeTemperature`
   - `relativeHumidity`
   - `windSpeed`
   - `windGust`
   - `windDirection`
   - `cloudCover`
   - `seaLevelPressure`
   - `totalPrecipitation`
   - `conditionCode`
5. Jei lauko atsakyme nėra, langelyje rašyk „nėra“. Nieko neapskaičiuok ir neišversk `conditionCode` į lietuvišką aprašą, jei API jo nedavė.
6. Jei API nepasiekiamas, atidaryk https://www.meteo.lt/prognozes/lietuvos-miestai/ ir užpildyk tik tuos stulpelius, kuriuos puslapis tikrai rodo. Kitus pažymėk „nėra“.
7. Patikrink, ar lentelėje yra visos penkios eilutės. Trūkstamo miesto nekeisk kitu ir nepalik tuščios eilutės be paaiškinimo.

Vienetai, kuriuos naudoja šis API: temperatūra °C, vėjas ir gūsiai m/s, kryptis laipsniais, debesuotumas ir drėgmė procentais, slėgis hPa, krituliai mm.

## Atsakymo formatas

Atsakyk lietuvių kalba. Viena lentelė:

| Miestas | Prognozės laikas | Temp. °C | Juntamoji °C | Drėgmė % | Vėjas m/s | Gūsiai m/s | Kryptis ° | Debesuotumas % | Slėgis hPa | Krituliai mm | Sąlygų kodas |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|

Po lentele nurodyk:

- **Patikrinimo laikas:** Lietuvos laiku.
- **Prognozės sudarymo laikas:** `forecastCreationTimeUtc`.
- **Tipas:** `forecastType`. Parašyk, kad tai prognozė, ne stoties stebėjimas.
- **Šaltinis:** [Meteo.lt API](https://api.meteo.lt/).

## Apribojimai

- Neimk temperatūrų iš atminties. Kiekviena reikšmė turi būti iš ką tik gauto atsakymo.
- Nedaryk daugiau kaip vienos prognozės užklausos miestui.
- Nerodyk visos kelių dienų sekos, jei prašoma dabartinės suvestinės.
- Jei šaltinis neveikia, parašyk tai atskirai ir nepalik lentelės su sugalvotais skaičiais.
