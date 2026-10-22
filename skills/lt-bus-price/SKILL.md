---
name: lt-bus-price
description: Paima pigiausią suaugusiojo autobuso bilietą vienai krypčiai tarp dviejų didžiųjų Lietuvos miestų iš autobusubilietai.lt. Naudok, kai jau yra maršruto kortelė su autobuso kodais ir data, ir reikia tik autobuso kainos.
---

# Autobuso kaina

## Tikslas

Pagal `lt-trip-route` kortelę paimk vieną pigiausią parduodamą autobuso bilietą. Traukinio neieškok ir transporto tarpusavyje nelygink.

Jei kortelės nėra, pirmiausia paruošk ją pagal `lt-trip-route`. Be kortelės kodų nespėk.

## Užklausa

`POST https://api.autobusubilietai.lt/api/route/search`

Antraštė `Content-Type: application/json`. Kūnas:

```json
{
  "origin": "2412-5,2412-1",
  "destination": "2408-1",
  "departuretime": "2026-10-23 00:00:00",
  "prices": "1",
  "isback": "0",
  "forward": "1",
  "onlyDirect": false,
  "onlyInternet": false,
  "onlyBikes": false
}
```

`origin` ir `destination` imk iš kortelės. `departuretime` yra kortelės data ir `00:00:00`.

## Kaina

Lauką `price` grąžina euro centais. Eurais rodyk `price / 100` su dviem skaičiais po kablelio. Centų į eurus neversk atvirkščiai ir kainos iš kito šaltinio neperrašyk.

Tinkamas variantas yra `data.routes` įrašas, kurio pirma koja `legs[0]` turi `sellable: true` ir `price` didesnį už nulį. Iš jų rink pigiausią. Jei kaina vienoda, rink ankstesnį išvykimą.

Jei atsakymas ne `200`, `status` nėra `OK`, arba tinkamo varianto nėra, rašyk „nėra“. Tuščios kainos nekeisk spėjamu skaičiumi.

## Rezultatas

```text
Autobusas: {miestas} → {miestas}
Data: {YYYY-MM-DD}
Išvykimas: {departureTime.text}
Atvykimas: {arrivalTime.text}
Maršrutas: {legs[0].title}
Kaina: {price / 100} EUR
Šaltinis: https://www.autobusubilietai.lt/
```

`Maršrutas` perrašyk iš `legs[0].title`. Jei pavadinime yra daugiau miestų, jų neišmesk. Laikus imk iš `departureTime.text` ir `arrivalTime.text`. Pavyzdžio skaičių nekopijuok: kiekvieną kartą imk tik tą atsakymą.
