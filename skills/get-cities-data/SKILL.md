---
name: get-cities-data
description: Surenka penkių didžiausių Lietuvos miestų meteorologinius duomenis iš Meteo.lt ir dar keturių viešų orų šaltinių, tada pateikia juos vienoje lentelėje. Naudok, kai prašoma palyginti temperatūrą, vėją, drėgmę, slėgį, debesuotumą ar kritulius iš kelių orų svetainių.
---

# Miestų meteorologiniai duomenys

## Tikslas

Vienoje lentelėje pateikti Vilniaus, Kauno, Klaipėdos, Šiaulių ir Panevėžio duomenis iš penkių šaltinių. Kiekvienam miestui yra penkios eilutės, po vieną šaltiniui. Tuščias langelis rašomas „nėra“. Trūkstamų skaičių nekurk.

Koordinatės paimtos iš `https://api.meteo.lt/v1/places/{kodas}`. Kitų koordinačių nenaudok.

| Miestas | Platuma | Ilguma |
|---|---:|---:|
| Vilnius | 54.68705 | 25.28291 |
| Kaunas | 54.89821 | 23.90448 |
| Klaipėda | 55.71275 | 21.13505 |
| Šiauliai | 55.93408 | 23.31578 |
| Panevėžys | 55.73450 | 24.35781 |

## Šaltiniai

Kiekvienam miestui atlik po vieną užklausą į kiekvieną šaltinį.

1. **Meteo.lt.** `https://api.meteo.lt/v1/places/{kodas}/forecasts/long-term`. Kodai: `vilnius`, `kaunas`, `klaipeda`, `siauliai`, `panevezys`. Imk `forecastTimestamps` įrašą, kurio `forecastTimeUtc` artimiausias dabartiniam Lietuvos laikui. Laukai: `airTemperature`, `feelsLikeTemperature`, `relativeHumidity`, `windSpeed`, `windGust`, `windDirection`, `cloudCover`, `seaLevelPressure`, `totalPrecipitation`, `conditionCode`. Vienetai: °C, %, m/s, laipsniai, hPa, mm.
2. **Open-Meteo.** `https://api.open-meteo.com/v1/forecast?latitude={platuma}&longitude={ilguma}&current=temperature_2m,relative_humidity_2m,apparent_temperature,precipitation,weather_code,cloud_cover,pressure_msl,wind_speed_10m,wind_direction_10m,wind_gusts_10m`. Vienetus imk iš atsakymo `current_units`, ne iš atminties.
3. **MET Norway.** `https://api.met.no/weatherapi/locationforecast/2.0/compact?lat={platuma}&lon={ilguma}`. Siųsk antraštę `User-Agent` su projekto pavadinimu. Imk pirmą `timeseries` įrašo `instant.details`. Atsakyme vienetų pavadinimų nėra, todėl skaičių neversk ir prie jų nepridėk spėjamų vienetų. Užrašyk lauko pavadinimą.
4. **wttr.in.** `https://wttr.in/{miestas}?format=j1`. Miestų vardai užklausoje: `Vilnius`, `Kaunas`, `Klaipeda`, `Siauliai`, `Panevezys`. Imk `current_condition`: `temp_C`, `FeelsLikeC`, `humidity`, `windspeedKmph`, `winddirDegree`, `cloudcover`, `pressure`, `precipMM`, `weatherDesc`. Užsirašyk ir `nearest_area`. Jei jis nesutampa su prašytu miestu, prie eilutės pridėk tą vietovės vardą.
5. **7Timer.** `https://www.7timer.info/bin/api.pl?lon={ilguma}&lat={platuma}&product=civil&output=json`. Imk `dataseries` įrašą su mažiausiu `timepoint`. `temp2m` yra temperatūra. `cloudcover`, `rh2m`, `prec_amount`, `wind10m` ir `weather` perrašyk taip, kaip grąžinta. Vėjo greičio neverk į m/s.

Jei šaltinis neatsako, to šaltinio penkioms eilutėms visuose duomenų langeliuose rašyk „nėra“. Kito šaltinio skaičiais jų neužpildyk.

## Atsakymo formatas

Atsakyk lietuvių kalba. Viena lentelė, 25 eilutės:

| Miestas | Šaltinis | Laikas | Temperatūra | Juntamoji | Drėgmė | Vėjas | Gūsiai | Kryptis | Debesuotumas | Slėgis | Krituliai | Sąlygos |
|---|---|---|---|---|---|---|---|---|---|---|---|---|

Po lentele nurodyk patikrinimo laiką Lietuvos laiku ir penkias šaltinių nuorodas: [Meteo.lt](https://api.meteo.lt/), [Open-Meteo](https://open-meteo.com/), [MET Norway](https://api.met.no/), [wttr.in](https://wttr.in/), [7Timer](https://www.7timer.info/). Parašyk, kad tai prognozės, ne vienos stoties stebėjimas.

## Apribojimai

- Kiekviena reikšmė turi būti iš ką tik gauto to šaltinio atsakymo.
- Nedaryk daugiau kaip vienos užklausos vienam miestui ir vienam šaltiniui.
- Nerodyk kelių dienų sekos, jei prašoma dabartinės suvestinės.
- `conditionCode`, `weather_code` ir 7Timer `weather` palik tokius, kokius grąžino šaltinis.
